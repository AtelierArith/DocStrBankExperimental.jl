```
lad(X, y, exact = true)
```

与えられた回帰設定に対して最小絶対偏差回帰を実行します。

# 引数

  * `X::AbstractMatrix{Float64}`: 線形モデルのデザイン行列。
  * `y::AbstractVector{Float64}`: 線形モデルの応答ベクトル。
  * `exact::Bool`: true の場合、正確な LAD 回帰を使用します。false の場合、GA を使用して LAD 回帰パラメータを推定します。デフォルトは true です。
