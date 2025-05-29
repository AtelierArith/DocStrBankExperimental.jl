```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::ExtrinsicEstimation;
    kwargs...,
)
```

`x`の中央値を[`ExtrinsicEstimation`](@extref `ManifoldsBase.ExtrinsicEstimation`)を使用して推定します。つまり、埋め込み内で中央値を計算し、結果を元に戻します。

`kwargs`の説明については、[`median`](@ref median(::AbstractManifold, ::AbstractVector, ::AbstractVector, ::CyclicProximalPointEstimation))を参照してください。
