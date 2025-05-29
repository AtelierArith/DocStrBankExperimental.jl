```
BrierLoss()
```

呼び出し可能な指標を返し、ブライヤー損失を計算します。エイリアス: `brier_loss`, `cross_entropy`, `quadratic_loss`.

```
BrierLoss()(ŷ, y)
BrierLoss()(ŷ, y, weights)
BrierLoss()(ŷ, y, class_weights::AbstractDict)
BrierLoss()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `BrierLoss()` を評価し、真の観測値 `y` を与えます。詳細については、符号が異なるだけの [`BrierScore`](@ref) を参照してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(BrierLoss(), ŷ, y)` を使用します。一般に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Missing,T}` を満たすことが期待され、ここで `T` は `Continuous` または `Count`（それぞれ `ŷ` の連続または離散の Distribution.jl オブジェクト）または `OrderedFactor` または `Multiclass`（`ŷ` の `UnivariateFinite` 分布の場合）です。

利用可能な指標の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行します。

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
