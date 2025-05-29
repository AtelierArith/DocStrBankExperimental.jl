```
dither([T::Type,] img, alg::AbstractDither, ncolors; maxiter, tol, kwargs...)
```

画像 `img` をアルゴリズム `alg` を使用してディザリングします。サイズ `ncolors` のカラーパレットは、ColorQuantization.jl の `KMeansQuantization` によって計算され、K-means クラスタリングが適用されます。
