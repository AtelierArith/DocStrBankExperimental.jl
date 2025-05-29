```
AuROC(y::AbstractVector{Bool}, yhat::AbstractVector)
```

受信者動作特性曲線の下の面積を台形法を使用して計算します。

# 引数

  * `y::AbstractArray`: バイナリクラスラベル。正のクラスには1、そうでない場合は0。
  * `̂yhat::AbstractArray`: 予測スコア。
