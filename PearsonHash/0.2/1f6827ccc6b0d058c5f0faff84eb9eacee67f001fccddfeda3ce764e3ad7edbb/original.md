```
hash8(data::Vector{UInt8}; seed::UInt8 = zero(UInt8))
hash8(data::AbstractString; seed::UInt8 = zero(UInt8))
```

Compute the Pearson 8-bit hash for `data` (optionally specify `seed`).
