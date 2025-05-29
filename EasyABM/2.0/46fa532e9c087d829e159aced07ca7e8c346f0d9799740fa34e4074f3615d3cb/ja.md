```julia
adjacency_matrix(
    g::EasyABM.DirPropGraph
) -> SparseArrays.SparseMatrixCSC{Int64, Int64}

```

与えられた有向プロパティグラフのスパース行列としての隣接行列を返します。
