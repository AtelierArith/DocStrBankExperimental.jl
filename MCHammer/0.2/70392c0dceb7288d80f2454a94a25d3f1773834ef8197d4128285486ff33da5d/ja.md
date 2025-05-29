履歴系列に対して二重指数平滑法を適用します。

```
es_smooth(m::DoubleES, HistoricalSeries::Vector{<:Real})
```

# 引数

  * `m::DoubleES`: `alpha` と `beta` を持つ DoubleES モデル。
  * `HistoricalSeries`: 歴史的データのベクトル。

# 戻り値

以下を含む DataFrame：

  * `level`: 平滑化されたレベル値。
  * `trend`: 推定されたトレンド値。
  * `smoothed`: レベルとトレンドの合計。
