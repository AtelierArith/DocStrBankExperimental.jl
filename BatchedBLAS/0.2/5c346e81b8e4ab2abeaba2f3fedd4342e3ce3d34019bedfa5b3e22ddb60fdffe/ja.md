```
batched_ger!(alpha, x, y, A)
```

行列 `A` のインプレースランク1更新を行い、ベクトル `x` と `y` を使用して `alpha[k] * x[:,k] * transpose(y[:,k]) + A[:,:,k]` をすべての `k` に対して計算します。すべての入力は、AbstractFloats または Integers のいずれかの eltype を持つことができます。`alpha` はスカラーでも構いません。
