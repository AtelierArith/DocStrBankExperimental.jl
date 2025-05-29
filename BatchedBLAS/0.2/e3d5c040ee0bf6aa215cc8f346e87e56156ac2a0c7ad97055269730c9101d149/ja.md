```
batched_spmv!(ul, alpha, A, x, beta, y)
```

インプレースバッチ行列-ベクトル乗算と加算であり、すべての `k` に対して `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` に相当します。`A` はパックされた対称行列でなければならず、`uplo` は上三角 ('U') または下三角 ('L') がパックされているかを指定します。他のすべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。`alpha` と `beta` もスカラーであることができます。
