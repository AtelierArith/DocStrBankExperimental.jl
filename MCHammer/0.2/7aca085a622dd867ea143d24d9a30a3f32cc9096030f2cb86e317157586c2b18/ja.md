ダブル指数平滑法を使用して予測を生成します。

```
es_forecast(m::DoubleES, HistoricalSeries::Vector{<:Real}, periods::Int)
```

# 引数

  * `m::DoubleES`: `alpha` と `beta` を持つ DoubleES モデル。
  * `HistoricalSeries`: 歴史的データのベクトル。
  * `periods`: 歴史的データを超えて予測する期間の数。

# 戻り値

`Historical`、`Level`、および `Forecast` の列を持つ DataFrame。
