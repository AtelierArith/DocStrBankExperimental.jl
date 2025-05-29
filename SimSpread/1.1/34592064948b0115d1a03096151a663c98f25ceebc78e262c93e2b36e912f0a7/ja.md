```
maxperformance(y::AbstractVector{Bool}, yhat::AbstractVector{Float64}, metric::Function)
```

与えられたメトリックの最大パフォーマンスをラベル-予測ベクトルのペアに対して取得します。

# 引数

  * `y::AbstractVector{Bool}`: バイナリクラスラベル。正のクラスには1、そうでない場合は0。
  * `̂yhat::AbstractVector{Float64}`: 予測スコア。
  * `̂metric::Function`: 評価に使用するパフォーマンスメトリック関数。
