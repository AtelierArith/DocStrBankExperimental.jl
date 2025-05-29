```
mean(
    M::Rotations,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/2/√2);
    kwargs...,
)
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` using [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`).
