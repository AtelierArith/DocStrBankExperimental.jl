```
get_mutual_information(xy; <keyword arguments>)
```

# 引数:

  * `xy`: 2Dの頻度または確率。
  * `estimator="maximum_likelihood"`: エントロピー推定器。
  * `base=2`: 対数の基数、情報の単位に相当。
  * `probabilities=false`: `xy`が確率であるかどうか。`false`の場合、`xy`は頻度。
  * `lambda=nothing`: 縮小強度、`estimator`が`"shrinkage"`の場合のみ使用。
  * `prior=1`: ディリクレ事前分布、`estimator`が`"dirichlet"`の場合のみ使用。
