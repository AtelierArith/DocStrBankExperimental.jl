履歴系列に対して単純指数平滑法を実行します。

```
es_smooth(m::SimpleES, HistoricalSeries::Vector{<:Real}; forecast_only::Bool=false)
```

# 引数

  * `m::SimpleES`: スムージング定数 `alpha` を含む SimpleES モデル。
  * `HistoricalSeries`: 履歴データのベクトル。
  * `forecast_only` (オプション): true の場合、平滑化された予測のみが返されます。

# 戻り値

平滑化された値のデータフレーム、または元の値と平滑化された値。
