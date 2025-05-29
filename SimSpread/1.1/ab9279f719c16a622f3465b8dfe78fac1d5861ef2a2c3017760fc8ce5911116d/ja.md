```
recallatL(y, yhat, L)
```

Wuら（2017）によって提案されたrecall@Lを取得します。

# 引数

  * `y::AbstractVector`: バイナリクラスラベル。正のクラスは1、その他は0。
  * `̂yhat::AbstractVector`: 予測スコア。
  * `L::Integer`: メトリクスを計算するために考慮する長さ（デフォルト = 20）。
