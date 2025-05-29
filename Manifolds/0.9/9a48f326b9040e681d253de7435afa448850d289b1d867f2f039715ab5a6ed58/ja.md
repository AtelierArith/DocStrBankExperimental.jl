```
mean(
    M::GeneralizedGrassmann,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/4);
    kwargs...,
)
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を `x` に対して計算し、[`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`) を使用します。
