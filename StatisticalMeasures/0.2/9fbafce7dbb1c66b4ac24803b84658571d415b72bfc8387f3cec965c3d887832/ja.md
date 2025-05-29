```
RootMeanSquaredError()
```

ルート平均二乗誤差を計算するための呼び出し可能な測定値を返します。エイリアス: `rms`, `rmse`, `root_mean_squared_error`.

```
RootMeanSquaredError()(ŷ, y)
RootMeanSquaredError()(ŷ, y, weights)
RootMeanSquaredError()(ŷ, y, class_weights::AbstractDict)
RootMeanSquaredError()(ŷ, y, weights, class_weights::AbstractDict)
```

予測 `ŷ` に対して `RootMeanSquaredError()` を評価し、真の観測値 `y` を考慮します。具体的には、すべての観測ペア `(ŷ_i, y_i)` に対して $|y_i-ŷ_i|^2$ の平均を計算し、その結果の平方根を返します。一般的には、指定された重みで二乗偏差を前乗算します。

`Real` 要素を生成する `length` を持つ任意のイテレータを `weights` に使用できます。`class_weights` のキーは `y` の観測値のすべての考えられる値を含む必要があり、値は `Real` である必要があります。

測定値は集約されます。各観測値の別々の測定値を取得するには、構文 `measurements(RootMeanSquaredError(), ŷ, y)` を使用します。一般的に、`MLUtils.eachobs(y)` の観測値 `obs` は `ScientificTypes.scitype(obs)<:``Union{Infinite,Missing}`` を満たすことが期待されます。

利用可能な測定値の完全な辞書を取得するには、コンストラクタに基づいてキー付けされた [`measures()`](@ref) を実行します。

# 特性

```
consumes_multiple_observations = true
can_report_unaggregated = true
kind_of_proxy = LearnAPI.Point()
observation_scitype = Union{Missing, ScientificTypesBase.Infinite}
can_consume_tables = false
supports_weights = true
supports_class_weights = true
orientation = StatisticalMeasuresBase.Loss()
external_aggregation_mode = StatisticalMeasuresBase.RootMean{Int64}(2)
human_name = root mean squared error
```
