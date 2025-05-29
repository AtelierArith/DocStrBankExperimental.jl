```
mean(M::AbstractManifold, x::AbstractVector[, w::AbstractWeights]; kwargs...)
```

ベクトル `x` の点の（オプションで重み付けされた）リーマン中心を計算します。これは、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M` 上の点であり、最小化条件を満たす点として定義されます。

$$
\operatorname{argmin}_{y ∈ \mathcal M} \frac{1}{2 \sum_{i=1}^n w_i} \sum_{i=1}^n w_i\mathrm{d}_{\mathcal M}^2(y,x_i),
$$

ここで、$\mathrm{d}_{\mathcal M}$ はリーマンの[`距離`](@ref)を示します。

一般的な場合、[`GradientDescentEstimation`](@extref `ManifoldsBase.GradientDescentEstimation`) が平均を計算するために使用されます。     mean(         M::AbstractManifold,         x::AbstractVector,         [w::AbstractWeights,]         method::AbstractApproximationMethod=default*approximation*method(M, mean);         kwargs...,     )

指定された `method` を使用して平均を計算します。

```
mean(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::GradientDescentEstimation;
    p0=x[1],
    stop_iter=100,
    retraction::AbstractRetractionMethod = default_retraction_method(M),
    inverse_retraction::AbstractInverseRetractionMethod = default_retraction_method(M, eltype(x)),
    kwargs...,
)
```

勾配降下法スキーム [`GradientDescentEstimation`](@extref `ManifoldsBase.GradientDescentEstimation`) を使用して平均を計算します。

オプションで、`p0`（デフォルトでは最初のデータポイントに設定）を開始点として提供します。`stop_iter` は実行する最大反復回数を示し、`kwargs...` は、2つの反復間の最小変化が小さいときに停止するために [`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`) に渡されます。停止基準の詳細については、[`Manopt.jl`](https://manoptjl.org) パッケージを確認し、そこからソルバーを使用してください。

オプションで、（逆）再tractionを指定するために `retraction` と `inverse_retraction` メソッドタイプを渡します。

理論は [Karcher:1977](@cite) に由来し、[PennecArsigny:2012](@cite) では指数バリセンターとしても説明されています。アルゴリズムはさらに[AfsariTronVidal:2013](@cite)で説明されています。 ```
