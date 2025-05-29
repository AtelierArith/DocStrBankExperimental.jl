```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GeodesicInterpolationWithinRadius;
    kwargs...,
)
```

Estimate the Riemannian center of mass of `x` using [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`).

See [`mean`](@ref mean(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::GeodesicInterpolation)) for a description of `kwargs`.
