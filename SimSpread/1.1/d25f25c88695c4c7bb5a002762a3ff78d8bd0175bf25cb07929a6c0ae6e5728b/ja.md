```
precisionatL(y, yhat, grouping, L)
```

Wuら（2017）によって提案されたように、グループごとの平均precision@Lを取得します。

# 引数

  * `y::AbstractVector`: バイナリクラスラベル。正のクラスは1、その他は0。
  * `̂yhat::AbstractVector`: 予測スコア。
  * `grouping::AbstractVector`: グループラベル。
  * `L::Integer`: メトリクスを計算するために考慮する長さ（デフォルト = 20）。
