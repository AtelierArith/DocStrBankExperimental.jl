トリプル指数平滑法の最適パラメータをランダムトライアルで自動的にフィットします。

```
es_fit(::Type{TripleES}, HistoricalSeries::Vector{<:Real}, season_length::Int, trials::Int)
```

# 引数

  * `HistoricalSeries`: 歴史的データのベクトル。
  * `season_length`: 季節の期間数。
  * `trials`: 実行するランダムトライアルの数。

# 戻り値

最良のパラメータ（最小予測誤差）を持つ `TripleES` インスタンス。
