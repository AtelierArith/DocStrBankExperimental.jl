```julia
dynamic_dir_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.MortalType, EasyABM.DirGType}}

```

与えられた隣接行列のための有向プロップグラフを作成します。
