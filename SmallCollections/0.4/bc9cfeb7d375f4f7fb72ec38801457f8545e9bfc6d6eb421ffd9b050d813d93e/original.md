```
resize(v::AbstractSmallVector{N,T}, n::Integer) -> SmallVector{N,T}
```

Return a vector of length `n` by making `v` longer or shorter. If the new vector is longer, then the new elements are initialized with `default(T)`.

See also `Base.resize!`, [`SmallCollections.default`](@ref).
