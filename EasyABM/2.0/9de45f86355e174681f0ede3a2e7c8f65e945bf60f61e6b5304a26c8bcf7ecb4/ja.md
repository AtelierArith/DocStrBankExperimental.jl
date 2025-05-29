```julia
static_dir_graph(
    A::SparseArrays.SparseMatrixCSC{Int64, Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.StaticType, EasyABM.DirGType}}

```

与えられたスパース行列としての隣接行列のための有向プロップグラフを作成します。
