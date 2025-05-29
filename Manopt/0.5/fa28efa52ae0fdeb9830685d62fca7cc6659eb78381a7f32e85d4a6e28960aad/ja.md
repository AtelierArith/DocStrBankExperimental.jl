```
StopWhenGradientNormLess <: StoppingCriterion
```

現在の勾配ノルムに基づく停止基準。

# フィールド

  * `norm`:      関数 `(M::AbstractManifold, p, X) -> ℝ` で、`M` 上の点 `p` での接空間における勾配 `X` のノルムを計算します。成分を持つ多様体の場合は、`(M::AbstractManifold, p, X, r) -> ℝ` を提供します。
  * `threshold`: この値未満の距離のときに停止することを示すしきい値
  * `outer_norm`: `M` が成分を持つ多様体である場合、要素ごとの距離に基づいて全体の距離を計算するために使用されるノルムを指定するために使用できます。

# 内部フィールド

  * `last_change` 最後の変更を保存
  * `at_iteration` 停止の指示があったイテレーションを保存

# 例

[`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) のような $\mathcal M = \mathcal N^n$ では、任意の点 $p = (p_1,…,p_n) ∈ \mathcal M$ は長さ $n$ のベクトルで、点 $p_i ∈ \mathcal N$ から構成されます。次に、`outer_norm` を $r$ として、現在の勾配 $X ∈ \mathcal M$ の接ベクトルのノルムは次のように与えられます。

```
\lVert X \rVert_{p} = \Bigl( \sum_{k=1}^n \lVert X_k \rVert_{p_k}^r \Bigr)^{\frac{1}{r}},
```

ここで、$r=∞$ の場合、合計は最大値に変わります。`outer_norm` は成分を持たない多様体には影響しません。

個別のノルムを渡す場合、`outer_norm` に `missing` を渡すことで、そのような多様体では無効にできます。

# コンストラクタ

```
StopWhenGradientNormLess(ε; norm=ManifoldsBase.norm, outer_norm=missing)
```

勾配のしきい値 `ε` を持つ停止基準を作成します。つまり、この基準は [`get_gradient`](@ref) がノルムが `ε` 未満の勾配ベクトルを返すときに停止することを示します。使用するノルムは `norm=` キーワードで指定できます。
