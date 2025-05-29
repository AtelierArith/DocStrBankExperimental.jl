```
fnv1(T, p::Ptr{UInt8}, n::Integer)
fnv1(T, x::Union{String, DenseVector{UInt8}})
```

Calculate the Fowler-Noll-Vo version 1 hash of the input for the bitwidth defined by T. T must unsigned.
