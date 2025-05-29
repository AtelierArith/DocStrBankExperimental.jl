```
batched_gemv!(tA, alpha, A, x, beta, y)
```

インプレースのバッチ行列ベクトル乗算と加算であり、すべての `k` に対して `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` に相当します。`A` はオプションで `tA` を使って `N`、`T`、または `C` として転置できます。他のすべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。`alpha` と `beta` もスカラーであることができます。
