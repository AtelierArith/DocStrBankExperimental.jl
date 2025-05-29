```
hash256(x::Block) -> Vector{UInt8}
hash256(x::Header) -> Vector{UInt8}
hash256(x::Tx) -> Vector{UInt8}
```

Returns the reversed double sha256 of a `Block`, `Header`, or `Tx` serialization. `Tx` is always serialized as a legacy transaction.

```julia
hash256(block)
hash256(header)
hash256(transaction)
```
