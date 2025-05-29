```
adjacency_matrix(g::BipartiteIndexedGraph, T::DataType=Int)
```

左ノードと右ノードの区別をせずに、サイズ `nv(g) = nv_left(g) + nv_right(g)` の対称隣接行列を返します。
