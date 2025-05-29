```
get_redundancy(values_x, values_y, values_z; <keyword arguments>)
```

三つの値のセット間の冗長性を推定します。

# 引数:

  * `values_x`: データ値。
  * `values_y`: 二つ目のデータ値のセット。
  * `values_z`: 三つ目のデータ値のセット。
  * `estimator="maximum_likelihood"`: エントロピー推定器。
  * `base=2`: 対数の基数、情報の単位に相当します。
  * `mode="uniform_width"`: 離散化アルゴリズム。
  * `number_of_bins=0`: ビンの数（`mode`が`"bayesian_blocks"`の場合は上書きされます）。
  * `get_number_of_bins=get_root_n`: ビンの数を計算するためのメソッド（`number_of_bins`が`0`の場合のみ呼び出されます）。
  * `lambda=nothing`: 縮小強度、`estimator`が`"shrinkage"`の場合のみ使用されます。
  * `prior=1`: ディリクレ事前分布、`estimator`が`"dirichlet"`の場合のみ使用されます。
  * `all_orientations=false`: 各値のセットをターゲットとして使用するかどうか。`false`の場合、`values_z`のみがターゲットとなります。
