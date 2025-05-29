```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::CyclicProximalPointEstimation;
    p0=x[1],
    stop_iter=1000000,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x),),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x),),
    kwargs...,
)
```

[`CyclicProximalPointEstimation`](@extref `ManifoldsBase.CyclicProximalPointEstimation`)を使用して中央値を計算します。

オプションで、`p0`、開始点を指定できます（デフォルトでは最初のデータポイントに設定されています）。`stop_iter`は実行する最大反復回数を示し、`kwargs...`は[`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`)に渡され、2つの反復間の最小変化が小さいときに停止します。その他の停止基準については、[`Manopt.jl`](https://manoptjl.org)パッケージを確認し、そこからソルバーを使用してください。

オプションで、(逆)再tractionのメソッドタイプを渡して、(逆)再tractionを指定できます。

アルゴリズムの詳細は[Bacak:2014](@cite)に記載されています。
