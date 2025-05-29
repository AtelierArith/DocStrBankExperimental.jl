```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::ExtrinsicEstimation;
    kwargs...,
)
```

`x`のリーマン中心を[`ExtrinsicEstimation`](@extref `ManifoldsBase.ExtrinsicEstimation`)を使用して推定します。つまり、埋め込み内で平均を計算し、結果を再投影します。

残りの`kwargs`の説明については、[`mean`](@ref mean(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::GeodesicInterpolation))を参照してください。
