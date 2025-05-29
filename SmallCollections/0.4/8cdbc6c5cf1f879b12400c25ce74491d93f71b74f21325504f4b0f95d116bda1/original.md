```
setindex(v::AbstractFixedVector{N,T}, x, i::Integer) where {N,T} -> FixedVector{N,T}
```

Substitute `x` for the `i`-th component of `v` and return the result. The vector `v` is not modified.

See also `Base.setindex`,  [`addindex`](@ref addindex(::AbstractFixedVector, ::Any, ::Integer)).
