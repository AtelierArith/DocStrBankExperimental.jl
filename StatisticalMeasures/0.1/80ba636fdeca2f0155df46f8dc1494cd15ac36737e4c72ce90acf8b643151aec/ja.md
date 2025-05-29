```
MeanAbsoluteProportionalError(; tol=eps())
```

平均絶対比例誤差を計算するための呼び出し可能な測定値を返します。エイリアス: `mape`。

```
m(ŷ, y)
m(ŷ, y, weights)
m(ŷ, y, class_weights::AbstractDict)
m(ŷ, y, weights, class_weights::AbstractDict)
```

`MeanAbsoluteProportionalError` コンストラクタによって返される測定値 `m`（例: `m = MeanAbsoluteProportionalError()`）を、真の観測値 `y` に対して予測値 `ŷ` に評価します。具体的には、すべての観測ペア $(ŷ_i, y_i)$ に対して $|ŷ_i-y_i| \over |y_i|$ の平均を返します。一般的には、指定された重みで平均化される値を事前に乗算します。$|y_i|$<`tol` の項は合計から除外されますが、対応する重み（またはカウント）は平均正規化因子に寄与します。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(m, ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}` を満たすことが期待されます。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいて [`measures()`](@ref) を実行します。

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
human_name = mean absolute proportional error
```
