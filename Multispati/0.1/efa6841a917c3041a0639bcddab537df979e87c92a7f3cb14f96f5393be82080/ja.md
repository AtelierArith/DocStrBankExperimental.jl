```
fit(SpatialPCA, X, W; ...)
```

与えられた行列 `X` と `W` に対して SpatialPCA を実行します。 `X` の各列は **観測** です。 `W` は接続行列で、$w_{ij}$ は j -> i の接続を示します。

**キーワード引数**

  * `maxoutdim`: 出力次元、すなわち変換された空間の次元 (*min(d, nc-1)*)
  * `solver`: ソルバーの選択:

      * `:eig`: `LinearAlgebra.eigen` を使用 (*デフォルト*)
      * `:eigs`: `Arpack.eigs` を使用 (常にスパースデータに使用)
  * `tol`: `eigs` ソルバーの収束許容値 (*デフォルト* `0.0`)
  * `maxiter`: `eigs` ソルバーの最大反復回数 (*デフォルト* `300`)
  * `center_sparse`: スパース行列 `X` を中心化 (密な X は常に中心化されます) (*デフォルト* `false`)

**参考文献**

[T. Jombart, et al. "Revealing cryptic spatial patterns in genetic variability by a new multivariate method." *Heredity* (2008)](https://doi.org/10.1038/hdy.2008.34)
