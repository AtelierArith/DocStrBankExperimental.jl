トリプル指数平滑法（ホルト・ウィンターズ法）を使用して季節調整を行った予測を生成します。

```
es_forecast(m::TripleES, HistoricalSeries::Vector{<:Real}, periods_out::Int; forecast_only::Bool=false)
```

# 引数

  * `m::TripleES`: `season_length`、`alpha`、`beta`、および `gamma` を持つ TripleES モデル。
  * `HistoricalSeries`: 過去のデータのベクトル。
  * `periods_out`: 過去のデータを超えて予測する期間の数。
  * `forecast_only`（オプション）: true の場合、予測された値のみを返します。

# 戻り値

予測された値のベクトル（`forecast_only=true` の場合）または完全なインサンプル予測。
