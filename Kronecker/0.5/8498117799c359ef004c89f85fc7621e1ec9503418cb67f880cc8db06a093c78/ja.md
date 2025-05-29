```
eigen(K::AbstractKroneckerProduct)
```

`LinearAlgebra`パッケージの`eigen`のラッパー。`AbstractKroneckerProduct`インスタンスの行列が正方行列である場合、これらに対して固有値分解を行い、`Eigen`型を返します。そうでない場合は、インスタンスを収集し、全行列に対してeigenを実行します。関数`\`、`inv`、および`logdet`は、この型で効率的に動作するようにオーバーロードされています。
