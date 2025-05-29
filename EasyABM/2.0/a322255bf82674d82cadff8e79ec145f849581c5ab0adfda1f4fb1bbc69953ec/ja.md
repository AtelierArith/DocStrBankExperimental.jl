```julia
static_dir_graph(
    A::Matrix{Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.StaticType, EasyABM.DirGType}}

```

与えられた隣接行列のための有向プロップグラフを作成します。
