```
multi_adjacency_matrix_deltacomplex(D::DeltaComplex) :: Matrix{Int32}
```

デルタ複体 `D` の多重 *隣接行列* を計算します。

`i,j` 番目の値は、`i` 番目と `j` 番目の `TriFace` が隣接している側の数をカウントします。
