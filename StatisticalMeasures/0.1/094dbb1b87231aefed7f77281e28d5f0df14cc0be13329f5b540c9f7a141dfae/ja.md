```
LogCoshLoss()
```

呼び出し可能な測定値を返し、ログコサインハイパーボリック損失を計算します。エイリアス: `log_cosh`, `log_cosh_loss`。

```
LogCoshLoss()(ŷ, y)
LogCoshLoss()(ŷ, y, weights)
LogCoshLoss()(ŷ, y, class_weights::AbstractDict)
LogCoshLoss()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `LogCoshLoss()` を評価し、真の観測値 `y` を考慮します。すべての観測ペア $(ŷ_i, y_i)$ に対して $\log(\cosh(ŷ_i-y_i))$ の平均を返します。一般的には、指定された重みで平均化された値を前乗算します。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(LogCoshLoss(), ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}` を満たすことが期待されます。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行します。

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
external_aggregation_mode = StatisticalMeasuresBase.Mean()
human_name = log cosh loss
```
