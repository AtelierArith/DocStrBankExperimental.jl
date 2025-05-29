```
mean(
    M::ProbabilitySimplex,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolation();
    kwargs...,
)
```

Compute the Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) of `x` using [`GeodesicInterpolation`](@extref `ManifoldsBase.GeodesicInterpolation`).
