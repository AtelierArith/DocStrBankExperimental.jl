```
median(
    M::AbstractManifold,
    x::AbstractVector,
    [w::AbstractWeights,]
    method::WeiszfeldEstimation;
    α = 1.0,
    p0=x[1],
    stop_iter=2000,
    retraction::AbstractRetractionMethod = default_retraction_method(M, eltype(x)),
    inverse_retraction::AbstractInverseRetractionMethod = default_inverse_retraction_method(M, eltype(x)),
    kwargs...,
)
```

[`WeiszfeldEstimation`](@extref `ManifoldsBase.WeiszfeldEstimation`)を使用して中央値を計算します。

オプションで、`p0`（デフォルトでは最初のデータポイントに設定）を提供します。`stop_iter`は実行する最大反復回数を示し、`kwargs...`は[`isapprox`](@extref `Base.isapprox-Tuple{AbstractManifold, Any, Any, Any}`)に渡され、2つの反復間の最小変化が小さいときに停止します。その他の停止基準については、[`Manopt.jl`](https://manoptjl.org)パッケージを確認し、そこからソルバーを使用してください。

パラメータ$α\in (0,2]$はステップサイズです。

アルゴリズムは[FletcherVenkatasubramanianJoshi:2008](@cite)でさらに説明されており、特に式(6)の更新ルールに関して、$q_{k}$を現在の反復、$n$を点の数$x_1,\ldots,x_n$とし、

$$
I_k = \bigl\{ i \in \{1,\ldots,n\} \big| x_i \neq q_k \bigr\}
$$

現在の反復と等しくない点のすべてのインデックスを示します。次に、更新は$q_{k+1} = \exp_{q_k}(αX)$と読み取られ、ここで

$$
X = \frac{1}{s}\sum_{i\in I_k} \frac{w_i}{d_{\mathcal M}(q_k,x_i)}\log_{q_k}x_i
\quad
\text{ with }
\quad
s = \sum_{i\in I_k} \frac{w_i}{d_{\mathcal M}(q_k,x_i)},
$$

$$
\mathrm{d}_{\mathcal M}
$$

はリーマンの[`距離`](@ref)を示します。

オプションで、`retraction`および`inverse_retraction`メソッドタイプを渡して（逆）再tractionを指定します。デフォルトでは、それぞれ指数マップと対数マップが使用されます。
