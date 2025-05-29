```
serialize(program::Witness) -> Vector{UInt8}
```

Serialize a `Witness` data type starting with a `CompactSizeUInt` to indicate the number of stack items for the `TxIn`. It is followed by stack items, with each item starts with a `CompactSizeUInt` to indicate the length.
