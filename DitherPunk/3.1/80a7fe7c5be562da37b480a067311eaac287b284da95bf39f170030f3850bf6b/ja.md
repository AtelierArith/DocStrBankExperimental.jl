```
dither!([out,] img, alg::AbstractDither, ncolors; maxiter, tol, kwargs...)
```

アルゴリズム `alg` を使用して画像 `img` にディザリングを行います。サイズ `ncolors` のカラーパレットは、ColorQuantization.jl の `KMeansQuantization` によって計算され、K-means クラスタリングが適用されます。
