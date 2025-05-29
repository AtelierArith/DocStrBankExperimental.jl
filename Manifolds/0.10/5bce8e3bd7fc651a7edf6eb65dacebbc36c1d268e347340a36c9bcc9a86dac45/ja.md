```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GeodesicInterpolationWithinRadius;
    kwargs...,
)
```

`x`のリーマン中心を[`GeodesicInterpolationWithinRadius`](@extref `ManifoldsBase.GeodesicInterpolationWithinRadius`)を使用して推定します。

`kwargs`の説明については、[`mean`](@ref mean(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::GeodesicInterpolation))を参照してください。
