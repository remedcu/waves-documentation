# Predefined Functions in Smart Account language

| Function | Description |
| :--- | :--- |
| IsDefined | It checks if the option contains some value |
| Extract | Extract the value from the option |
| Some | To create the option |
| Size | It returns the size of byte array |
| txById | It returns the transaction by ID |
| getLong | It gets Long value from Data Transaction by Key |
| getBoolean | It gets boolean value from Data Transaction by Key |
| getbyteVector | It gets byte array fro Data Transaction by Key |
| addressFromPublicKey | It gets the address from a public key |
| addressFromString | It gets the address from string |

There is an important property that the **smart account** does not store any data on the blockchain. A **smart account** will only have access to blockchain state values that can be retrieved and executed relatively fast, in a “constant” time, for example to such fields as:

* Balances of accounts;

* Access to account state;

* Current Block’s properties \(e.g. height and timestamp\);

* Data stored in other transactions referenced by transactions \(e.g. proofs, DataTransaction\).

The types which will be used to predicate are **LONG, BOOLEAN, STRING, Option\[T\], byteVector, Nothing**.

An **Option\[T\] **can be either **Some\[T\]** or **None **object, which represents a missing value.

For example, if we want to get some transactions that do not exist in the blockchain we should receive **None**, but if this transaction is contained in the blockchain, the method should return **Some\(transaction\)**.

**Note.** A user cannot create new types; only predefined ones are available.

All constants will be declared in lazy **let** constructions, which delays the evaluation of an expression until its value is needed, and does it at most once. For instance: **let hash = blake2b\(preImage\)**.

The hash is not a variable: once created its values never change.

**SetScriptTransaction **sets the script which verifies all outgoing transactions. The set script can be changed by another **SetScriptTransaction** call unless it’s prohibited by a previously set script.

# Cryptographic Functions in Smart Account language

| Function | Description | Parameters |
| :--- | :--- | :--- |
| sigVerifyF | To verify and validate a signature | **Sign: **signature from transaction, we   use elliptic curve signature, version       curve25519.                                          **Message: **ByteVector **                           Public Key: **ByteVector |
| keccak256\(message\) | Hash computation for keccak256 | **Message:** byte array. |
| blake2b256\(message\) | Hash computation for blake2b256 | **Message:** byte array. |
| sha256\(message\) | hash computation for sha256 | **Message:** byte array. |


