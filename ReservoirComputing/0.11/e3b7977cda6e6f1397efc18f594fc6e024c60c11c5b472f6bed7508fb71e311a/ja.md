```
pseudo_svd([rng], [T], dims...; 
    max_value=1.0, sparsity=0.1, sorted=true, reverse_sort=false,
    return_sparse=false)
```

与えられた`sparsity`を使用してスパースリザーバ行列を構築するためのイニシャライザを返します。これは、[^\yang2018]で説明されている擬似SVDアプローチを使用しています。

# 引数

  * `rng`: ランダム数生成器。デフォルトはWeightInitializersの`Utils.default_rng()`です。
  * `T`: リザーバ行列の要素の型。デフォルトは`Float32`です。
  * `dims`: リザーバ行列の次元。

# キーワード引数

  * `max_value`: 行列内の要素の最大絶対値。デフォルトは1.0です。
  * `sparsity`: リザーバ行列の希望するスパースレベル。デフォルトは0.1です。
  * `sorted`: 対角行列を作成する前に特異値をソートするかどうかを示すブール値。デフォルトは`true`です。
  * `reverse_sort`: ソートされた特異値を逆にするかどうかを示すブール値。デフォルトは`false`です。
  * `return_sparse`: `sparse`行列を返すためのフラグ。デフォルトは`false`です。
  * `return_diag`: `Diagonal`行列を返すためのフラグ。`return_diag`と`return_sparse`の両方が`true`に設定されている場合、優先されるのは`return_diag`です。デフォルトは`false`です。

# 例

```jldoctest
julia> res_matrix = pseudo_svd(5, 5)
5×5 Matrix{Float32}:
 0.306998  0.0       0.0       0.0       0.0
 0.0       0.325977  0.0       0.0       0.0
 0.0       0.0       0.549051  0.0       0.0
 0.0       0.0       0.0       0.726199  0.0
 0.0       0.0       0.0       0.0       1.0
```

[^yang2018]: Yang, Cuili, et al. "*Design of polynomial echo state networks for time series prediction.*" Neurocomputing 290 (2018): 148-160.
