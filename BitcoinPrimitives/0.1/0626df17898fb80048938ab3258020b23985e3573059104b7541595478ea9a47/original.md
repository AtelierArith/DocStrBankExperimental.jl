```
Witness
```

Witness data type has a single `data` field, stored as `Vector{Vector{UInt8}}` in which each inner `Vector{UInt8}` represent a stack item.

The `Witness` is a serialization of all witness data of the transaction. Each `TxIn` is associated with a witness field. A witness field starts with a `CompactSizeUInt` to indicate the number of stack items for the `TxIn`. It is followed by stack items, with each item starts with a `CompactSizeUInt` to indicate the length. Witness data is NOT script.

A non-witness program `TxIn` MUST be associated with an empty witness field, represented by a `0x00`. If all `TxIn`s are not witness program, a transaction's `wtxid` is equal to its `txid`.
