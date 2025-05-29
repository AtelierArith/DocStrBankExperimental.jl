```
copy(M::AbstractManifold, p, X)
```

Copy the value(s) from the tangent vector `X` at a point `p` on the [`AbstractManifold`](@ref) `M` into a new tangent vector. See [`allocate_result`](@ref) for the allocation of new point memory and [`copyto!`](@ref) for the copying.
