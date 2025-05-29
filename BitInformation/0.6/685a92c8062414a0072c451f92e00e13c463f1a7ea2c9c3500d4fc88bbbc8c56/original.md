```
C = bitcount(A::AbstractArray{T}) where {T<:Union{Integer,AbstractFloat}}
```

Counts the occurences of the 1-bit in every bit position across all elements of `A`. Returns a counter array `C::Vector{Int}` such that the first entries represents the first bit in elements of type `T`, e.g. the sign bit for floats.
