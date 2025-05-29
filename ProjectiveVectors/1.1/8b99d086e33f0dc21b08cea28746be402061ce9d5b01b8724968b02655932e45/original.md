```
LinearAlgebra.dot(v::PVector{T, N}, w::PVector{T2, N}) where {T, T2, N}
```

Compute the component wise dot product. If decorated with `@inbounds` the check of the [`dims`](@ref) of `v` and `w` is skipped.
