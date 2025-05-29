```julia
adjacency_matrix(
    g::EasyABM.SimplePropGraph
) -> SparseArrays.SparseMatrixCSC{Int64, Int64}

```

与えられた単純なプロップグラフのスパース行列としての隣接行列を返します。
