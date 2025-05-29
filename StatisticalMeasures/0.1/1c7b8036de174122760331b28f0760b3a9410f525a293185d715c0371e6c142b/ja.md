```
BrierLoss()
```

Brier損失を計算するための呼び出し可能な測定値を返します。エイリアス: `brier_loss`, `cross_entropy`, `quadratic_loss`.

```
BrierLoss()(ŷ, y)
BrierLoss()(ŷ, y, weights)
BrierLoss()(ŷ, y, class_weights::AbstractDict)
BrierLoss()(ŷ, y, weights, class_weights::AbstractDict)
```

真の観測値 `y` に対して予測 `ŷ` で `BrierLoss()` を評価します。詳細については、符号が異なるだけの [`BrierScore`](@ref) を参照してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(BrierLoss(), ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Missing,T}` を満たすことが期待され、ここで `T` は `Continuous` または `Count`（それぞれ `ŷ` の連続または離散の Distribution.jl オブジェクト用）または `OrderedFactor` または `Multiclass`（`ŷ` の `UnivariateFinite` 分布用）です。

利用可能な測定値の完全な辞書を、コンストラクタに基づいて取得するには、[`measures()`](@ref) を実行してください。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Distribution()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite, ScientificTypesBase.Finite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = brier loss
```
