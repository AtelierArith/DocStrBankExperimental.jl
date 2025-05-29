```
mean(
    M::AbstractProjectiveSpace,
    x::AbstractVector,
    [w::AbstractWeights,]
    method = GeodesicInterpolationWithinRadius(π/4);
    kwargs...,
)
```

ベクトル `x` の点のリーマン平均 [`mean`](@ref mean(M::AbstractManifold, args...)) を [`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`) を使用して計算します。
