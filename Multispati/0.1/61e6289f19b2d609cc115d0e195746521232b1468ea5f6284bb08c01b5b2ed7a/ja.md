```
fit(MULTISPATI, X, W, Q=I, D=I / size(X, 2); ...)
```

与えられたデータに対して行列 `X` を用いて MULTISPATI を実行します。`X` の各列は **観測** です。`W` は接続行列で、$w_{ij}$ は j -> i の接続を示します。`Q` はサイズ `n` の対称行列（または LinearAlgebra.UniformScaling(@ref)）で、`D` はサイズ `d` の対称行列（または LinearAlgebra.UniformScaling(@ref)）です。

**キーワード引数**

  * `maxoutdim`: 出力次元、すなわち変換された空間の次元 (*min(d, nc-1)*)
  * `solver`: ソルバーの選択:

      * `:eig`: `LinearAlgebra.eigen` を使用 (*デフォルト*)
      * `:eigs`: `Arpack.eigs` を使用（常にスパースデータに使用される）
  * `tol`: `eigs` ソルバーの収束許容誤差 (*デフォルト* `0.0`)
  * `maxiter`: `eigs` ソルバーの最大反復回数 (*デフォルト* `300`)

**参考文献**

[S. Dray, et al. "Spatial ordination of vegetation data using a generalization of Wartenberg's  multivariate spatial correlation." *Journal of vegetation science* (2008)](https://doi.org/10.3170/2007-8-18312)

[de la Cruz and Holmes. "The duality diagram in data analysis: Examples of modern applications."  *The annals of applied statistics* (2011)](https://doi.org/10.1214/10-aoas408)
