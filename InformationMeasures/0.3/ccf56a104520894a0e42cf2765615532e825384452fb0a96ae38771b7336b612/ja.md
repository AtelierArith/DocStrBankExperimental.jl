```
get_total_correlation(xyz; <keyword arguments>)
```

# 引数:

  * `xyz`: 3D周波数または確率。
  * `estimator="maximum_likelihood"`: エントロピー推定器。
  * `base=2`: 対数の基数、情報の単位に相当。
  * `probabilities=false`: `xyz`が確率であるかどうか。`false`の場合、`xyz`は周波数。
  * `lambda=nothing`: 縮小強度、`estimator`が`"shrinkage"`の場合のみ使用。
  * `prior=1`: ディリクレ事前分布、`estimator`が`"dirichlet"`の場合のみ使用。
