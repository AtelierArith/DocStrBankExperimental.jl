```
RiskAdjustedCUSUM{G} <: AbstractStatistic
```

リスク調整CUSUMモニタリング統計。

# 引数

  * `Δ::Float64`: 検出されるロジスティック回帰モデルの線形予測子のシフト。
  * `model::G`: 予測に使用されるロジスティック回帰モデル。`predict(model, x)` 関数を持っている必要があります。
  * `response::Symbol`: `DataFrame`内の応答変数の名前。
  * `value::Float64`: 統計量の初期値。デフォルトは `0.0`。

# 参考文献

Steiner, S. H., Cook, R. J., Farewell, V. T., Treasure, T. (2000). リスク調整累積和チャートを使用した外科的パフォーマンスのモニタリング。Biostatistics, 1(4), 441-452. https://doi.org/10.1093/biostatistics/1.4.441 ```
