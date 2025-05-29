```
get_probabilities(estimator, frequencies; <keyword arguments>)
```

離散値のセットから確率を推定します。

# 引数:

  * `estimator`: エントロピー推定器。
  * `frequencies`: 離散化されたデータ値のビン頻度。
  * `lambda=nothing`: 縮小強度、`estimator`が`"shrinkage"`の場合のみ使用されます。
  * `prior=1`: ディリクレ事前分布、`estimator`が`"dirichlet"`の場合のみ使用されます。
