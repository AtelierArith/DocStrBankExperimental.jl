```
batched_syr!(uplo, alpha, x, A)
```

対称行列 `A` のインプレースランク-1更新を行います。ベクトル `x` を用いて、`alpha[k] * x[:,k] * transpose(x[:,k]) + A[:,:,k]` をすべての `k` に対して計算します。`A` は対称であると仮定されています。`A` の `uplo`（'U' または 'L' のいずれか）三角形のみが使用されます。他のすべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。`alpha` はスカラーでも構いません。
