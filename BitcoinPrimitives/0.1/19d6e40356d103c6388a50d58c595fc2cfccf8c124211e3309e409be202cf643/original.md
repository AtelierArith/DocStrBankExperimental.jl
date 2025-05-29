Bitcoin transactions are broadcast between peers in a serialized byte format, called raw format. It is this form of a transaction which is SHA256(SHA256()) hashed to create the TXID and, ultimately, the merkle root of a block containing the transaction—making the transaction format part of the consensus rules.

A raw transaction has the following top-level format:

  * Transaction version number; currently version 1 or 2. Programs creating

transactions using newer consensus rules may use higher version numbers. Version 2 means that BIP 68 applies.

  * A marker which MUST be a 1-byte zero value: `0x00` (BIP 141)
  * A flag which MUST be a 1-byte non-zero value: `0x01` (BIP 141)
  * Transaction inputs
  * Transaction outputs
  * A time (Unix epoch time) or block number (BIP 68)

A transaction may have multiple inputs and outputs, so the `TxIn` and `TxOut` structures may recur within a transaction.
