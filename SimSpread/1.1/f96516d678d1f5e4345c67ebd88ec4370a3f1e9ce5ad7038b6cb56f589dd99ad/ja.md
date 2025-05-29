```
AuPRC(y::AbstractVector{Bool}, yhat::AbstractVector)
```

トラペゾイダルルールを使用した精度-再現率曲線の下の面積。

# 引数

  * `y::AbstractArray`: バイナリクラスラベル。正のクラスには1、その他には0。
  * `̂yhat::AbstractArray`: 予測スコア。
