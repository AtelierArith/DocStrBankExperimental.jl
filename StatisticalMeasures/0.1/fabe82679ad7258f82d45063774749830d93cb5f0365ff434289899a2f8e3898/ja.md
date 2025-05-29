```
LPSumLoss(; p=2)
```

$$
L^p
$$

合計損失を計算するための呼び出し可能な測定値を返します。エイリアス: `l1_sum`, `l2_sum`.

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

`LPSumLoss` コンストラクタによって返された測定値 `m`（例: `m = LPSumLoss()`）を、真の観測値 `y` に対して予測値 `ŷ` で評価します。具体的には、すべての観測ペア $(ŷ_i, yᵢ)$ に対して $|ŷ_i - yᵢ|^p$ の（重み付き）合計を計算します。重み付き *平均* を使用するには、[`LPLoss`](@ref) を代わりに使用してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(m, ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`` を満たすことが期待されます。

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.LiteralTarget()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Sum()
human_name = ``L^p`` 合計損失
```
