```
StopWhenChangeLess <: StoppingCriterion
```

は、[`AbstractManoptSolverState`](@ref) `s` から最適化変数の変化のノルムを見ているのを停止するしきい値を保存します。つまり、`get_iterate(s)` にアクセスし、連続する反復を比較することによってです。保存には [`StoreStateAction`](@ref) が使用されます。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示した反復を示す整数で、ソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `last_change::Real`: この停止基準で記録された最後の変化
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆再traction $\operatorname{retr}^{-1}$、[再tractionとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照してください
  * `storage::StoreStateAction`: 前の反復にアクセスするためのストレージ
  * `at_iteration::Int`: この停止基準が最後にアクティブだった反復を示します。
  * `inverse_retraction`: この逆再tractionと接ベクトル空間上のノルムによって距離を近似するために渡すことができる [`AbstractInverseRetractionMethod`](@extref `ManifoldsBase.AbstractInverseRetractionMethod`)。これは、距離や対数写像が `M` で利用できない場合に使用できます。
  * `last_change`: 最後の変化を保存
  * `storage`: 前の反復にアクセスするための [`StoreStateAction`](@ref)。
  * `threshold`: 停止するためにチェックする変化のしきい値（下回ると停止）
  * `outer_norm`: `M` が成分を持つ多様体である場合、これは要素ごとの距離に基づいて全体の距離を計算するために使用されるノルムを指定するために使用できます。これを無効にするには、この値を `missing` に設定します。

# 例

[`AbstractPowerManifold`](@extref `ManifoldsBase.AbstractPowerManifold`) のような $\mathcal M = \mathcal N^n$ では、任意の点 $p = (p_1,…,p_n) ∈ \mathcal M$ は長さ $n$ のベクトルで、点 $p_i ∈ \mathcal N$ から成ります。次に、`outer_norm` を $r$ として、2つの点 $p,q ∈ \mathcal M$ の距離は次のように与えられます。

```
\mathrm{d}(p,q) = \Bigl( \sum_{k=1}^n \mathrm{d}(p_k,q_k)^r \Bigr)^{\frac{1}{r}},
```

ここで、$r=∞$ の場合、合計は最大値に変わります。`outer_norm` は成分を持たない多様体には影響しません。

多様体が成分を持たない場合、外部ノルムは無視されます。

# コンストラクタ

```
StopWhenChangeLess(
    M::AbstractManifold,
    threshold::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    inverse_retraction_method::IRT=default_inverse_retraction_method(M)
    outer_norm::Union{Missing,Real}=missing
)
```

は、[`StoreStateAction`](@ref) `a` を使用してしきい値 `ε` に停止基準を初期化します。デフォルトでは、`a` は単に `:Iterate` を保存するように初期化されています。また、`distance` のための逆再tractionメソッドや、そのデフォルトの逆再tractionを使用する多様体を提供することもできます。 ```
