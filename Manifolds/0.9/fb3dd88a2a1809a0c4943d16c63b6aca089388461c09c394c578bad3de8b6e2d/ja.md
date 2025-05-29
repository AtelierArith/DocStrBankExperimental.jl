```
median(M::AbstractManifold, x::AbstractVector[, w::AbstractWeights]; kwargs...)
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::AbstractApproximationMethod;
    kwargs...,
)
```

ベクトル `x` の点の（オプションで重み付けされた）リーマン中央値を、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M` 上で計算します。これは、次の最小化条件を満たす点として定義されます。

$$
\operatorname{argmin}_{y ∈ \mathcal M} \frac{1}{\sum_{i=1}^n w_i} \sum_{i=1}^n w_i\mathrm{d}_{\mathcal M}(y,x_i),
$$

ここで、$\mathrm{d}_{\mathcal M}$ はリーマンの[`距離`](@ref)を示します。この関数は滑らかではありません（すなわち微分不可能です）。

一般的な場合、[`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`) が中央値を計算するために使用されます。ただし、このデフォルトは特定の多様体に対してオーバーロードされる場合があります。

指定された `method` を使用して中央値を計算します。
