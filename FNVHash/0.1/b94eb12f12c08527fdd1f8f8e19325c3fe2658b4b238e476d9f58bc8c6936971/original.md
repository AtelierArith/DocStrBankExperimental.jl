```
fnv1a(T, p::Ptr{UInt8}, n::Integer)
fnv1a(T, x::Union{String, DenseVector{UInt8}})
```

Calculate the Fowler-Noll-Vo version 1a hash of the input for the bitwidth defined by T. T must unsigned.
