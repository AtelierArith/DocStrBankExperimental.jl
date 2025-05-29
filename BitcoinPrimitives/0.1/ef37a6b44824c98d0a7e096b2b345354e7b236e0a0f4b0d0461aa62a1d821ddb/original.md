```
serialize(tx::Tx; force_legacy::Bool=false) -> Vector{UInt8}
```

Returns the byte serialization of the transaction, force_legacy can optionally be set to true to serialize SegWit's (BIP 141) transaction as if they were legacy transaction to allow proper txid computation.
