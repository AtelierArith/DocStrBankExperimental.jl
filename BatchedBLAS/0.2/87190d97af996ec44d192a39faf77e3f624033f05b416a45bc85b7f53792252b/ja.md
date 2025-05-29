```
batched_symv!(uplo, alpha, A, x, beta, y)
```

インプレースバッチ行列ベクトル乗算と加算であり、すべての `k` に対して `y[:,k] = alpha[k] * A[:,:,k] * x[:,k] + beta[k] * y[:,k]` に相当します。 `A` は対称であると仮定されています。 `A` の `uplo`（'U' または 'L' のいずれか）三角形のみが使用されます。 他のすべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。 `alpha` と `beta` もスカラーであることができます。
