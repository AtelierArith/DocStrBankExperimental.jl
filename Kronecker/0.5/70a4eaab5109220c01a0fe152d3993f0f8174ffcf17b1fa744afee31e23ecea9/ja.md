```
cholesky(K::AbstractKroneckerProduct; check = true)
```

`LinearAlgebra`パッケージの`cholesky`のラッパーです。`AbstractKroneckerProduct`インスタンスの行列に対してCholesky分解を行い、`CholeskyKronecker`型を返します。`Cholesky`、`size`、`\`、`inv`、`det`、および`logdet`は、この型で効率的に動作するようにオーバーロードされています。
