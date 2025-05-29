```
M = trmatop(n, m)
M = trmatop(A)
```

すべての `n x m` 行列または `A` のサイズのすべての行列に対して、転置演算子 `M: X -> X'` を定義します。対応する交換行列（[こちら](https://en.wikipedia.org/wiki/Commutation_matrix)を参照）は `Matrix(M)` として生成できます。
