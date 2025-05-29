```
skewness(M::AbstractManifold, x::AbstractVector, k::Int[, w::AbstractWeights], m=mean(M, x[, w]))
```

Compute the standardized skewness of points in `x` on manifold `M`. Optionally provide weights `w` and/or a precomputed [`mean`](@ref mean(::AbstractManifold, args...)) `m`.
