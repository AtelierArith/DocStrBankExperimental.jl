```
addindex(v::AbstractFixedVector{N,T}, x, i::Integer) where {N,T} -> FixedVector{N,T}
```

Add `x` to the `i`-th component of `v` and return the result. The vector `v` is not modified.

See also [`setindex`](@ref setindex(::AbstractFixedVector, ::Any, ::Integer)).
