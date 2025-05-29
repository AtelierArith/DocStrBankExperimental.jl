歴史的系列と予測系列の間の分数標準誤差を計算します。

```
FrctStdError(HistoricalSeries::Vector{<:Real}, ForecastSeries::Vector{<:Real})
```

# 引数

  * `HistoricalSeries`: 歴史的データのベクトル。
  * `ForecastSeries`: 予測データのベクトル。

# 戻り値

標準誤差をFloat64として返します。
