```
get_conditional_mutual_information(xyz; <keyword arguments>)
```

# 引数:

  * `xyz`: 3Dの頻度または確率。
  * `estimator="maximum_likelihood"`: エントロピー推定器。
  * `base=2`: 対数の底、情報の単位に相当。
  * `probabilities=false`: `xyz`が確率であるかどうか。`false`の場合、`xyz`は頻度。
  * `lambda=nothing`: 縮小強度、`estimator`が`"shrinkage"`の場合のみ使用。
  * `prior=1`: ディリクレ事前分布、`estimator`が`"dirichlet"`の場合のみ使用。
