```
lta(X, y; exact = false)
```

与えられた回帰設定に対して、Hawkins & Olive (1999) アルゴリズム (最小トリム絶対偏差) を実行します。

# 引数

  * `X::AbstractMatrix{Float64}`: 線形回帰モデルの設計行列。
  * `y::AbstractVector{Float64}`: 線形回帰モデルの応答ベクトル。
  * `exact::Bool`: 回帰パラメータの数 p のすべての可能な部分集合を考慮するかどうか。
  * `earlystop::Bool`: 残りのイテレーション数 / 5 イテレーションで最良の目的が変わらない場合に早期停止します。

# 参考文献

Hawkins, Douglas M., and David Olive. "Applications and algorithms for least trimmed sum of  absolute deviations regression." Computational Statistics & Data Analysis 32.2 (1999): 119-134.
