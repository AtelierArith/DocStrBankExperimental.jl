```
mean(
    M::Grassmann,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/4);
    kwargs...,
)
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` using [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`).
