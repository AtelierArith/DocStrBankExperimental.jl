```
StopWhenGradientChangeLess <: StoppingCriterion
```

勾配の変化に基づく停止基準。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示したイテレーションを示す整数。これはソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `last_change::Real`: この停止基準で記録された最後の変化
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください
  * `storage::StoreStateAction`: 前のイテレーションにアクセスするためのストレージ
  * `threshold`: 変化をチェックするための閾値（停止するために下回る必要があります）
  * `outer_norm`: `M` が成分を持つ多様体である場合、これは要素ごとの距離に基づいて全体の距離を計算するために使用されるノルムを指定するために使用できます。これを無効にすることもできますが、この値を `missing` に設定します。

# 例

[`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) のような $\mathcal M = \mathcal N^n$ では、任意の点 $p = (p_1,…,p_n) ∈ \mathcal M$ は長さ $n$ のベクトルで、点 $p_i ∈ \mathcal N$ から構成されます。次に、`outer_norm` を $r$ として、接ベクトルの差のノルムは、最後の勾配 $X,Y ∈ \mathcal M$ のように次のように与えられます。

```
\lVert X-Y \rVert_{p} = \Bigl( \sum_{k=1}^n \lVert X_k-Y_k \rVert_{p_k}^r \Bigr)^{\frac{1}{r}},
```

ここで、$r=∞$ の場合、合計は最大値に変わります。`outer_norm` は、成分を持たない多様体には影響しません。

# コンストラクタ

```
StopWhenGradientChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    vector_transport_method::IRT=default_vector_transport_method(M),
    outer_norm::N=missing
)
```

勾配の変化に対する閾値 `ε` を持つ停止基準を作成します。つまり、この基準は [`get_gradient`](@ref) の変化のノルムが `ε` より小さいときに停止することを示します。ここで、`vector_transport_method` は使用されるベクトル輸送 $\mathcal T$ を示します。
