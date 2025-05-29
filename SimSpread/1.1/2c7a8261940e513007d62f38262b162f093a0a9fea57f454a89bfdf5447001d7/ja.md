```
BEDROC(y::AbstractVector{Bool}, yhat::AbstractVector; rev::Bool=true, α::AbstractFloat=20.0)
```

ボルツマン強化受信者動作特性（BEDROC）スコアは、*早期認識*の要素を許可する受信者動作特性（ROC）スコアの修正です。

スコアは、使用される予測モデルが（早期に）陽性クラスを検出する程度を示す[0, 1]の範囲の値を取ります。

# 引数

  * `y::AbstractArray`: バイナリクラスラベル。陽性クラスは1、その他は0。
  * `̂yhat::AbstractArray`: 予測スコア。
  * `rev::Bool`: $yhat$の高い値が陽性クラスと相関する場合は真（デフォルト = true）。
  * `α::AbstractFloat`: 早期認識パラメータ（デフォルト = 20.0）。

# 参考文献

1. Truchon, J.-F., & Bayly, C. I. (2007). Evaluating Virtual Screening Methods:  Good and

Bad Metrics for the “Early Recognition” Problem. Journal of Chemical Information and Modeling, 47(2), 488–508. https://doi.org/10.1021/ci600426e ```
