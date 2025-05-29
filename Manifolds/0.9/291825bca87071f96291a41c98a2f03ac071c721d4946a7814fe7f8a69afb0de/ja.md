```
mean(
    M::Rotations,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/2/√2);
    kwargs...,
)
```

Riemannian [`mean`](@ref mean(M::AbstractManifold, args...)) を使用して `x` の平均を計算します [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`)。
