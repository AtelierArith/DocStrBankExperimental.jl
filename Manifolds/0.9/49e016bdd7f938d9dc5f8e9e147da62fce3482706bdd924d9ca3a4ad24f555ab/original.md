```
mean(
    M::AbstractProjectiveSpace,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/4);
    kwargs...,
)
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of points in vector `x` using [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`).
