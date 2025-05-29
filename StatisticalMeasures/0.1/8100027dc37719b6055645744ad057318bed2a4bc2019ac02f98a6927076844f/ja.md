```
RootMeanSquaredLogError()
```

ルート平均二乗対数誤差を計算するための呼び出し可能な測定値を返します。エイリアス: `rmsl`, `rmsle`, `root_mean_squared_log_error`.

```
RootMeanSquaredLogError()(ŷ, y)
RootMeanSquaredLogError()(ŷ, y, weights)
RootMeanSquaredLogError()(ŷ, y, class_weights::AbstractDict)
RootMeanSquaredLogError()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `RootMeanSquaredLogError()` を評価し、真の観測値 `y` を考慮します。具体的には、すべての観測ペア `(ŷ_i, y_i)` に対して $(\log(y)_i - \log(ŷ_i))^2$ の平均を返し、その結果の平方根を返します。一般的には、指定された重みで平均化された値を前乗算します。オフセットを含めるには、[`RootMeanSquaredLogProportionalError`](@ref) を使用してください。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(RootMeanSquaredLogError(), ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`` を満たすことが期待されます。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行してください。

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
external_aggregation_mode = StatisticalMeasuresBase.RootMean{Int64}(2)
human_name = root mean squared log error
```
