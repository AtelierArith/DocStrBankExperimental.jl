```julia
dynamic_dir_graph(
    A::Matrix{Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.MortalType, EasyABM.DirGType}}

```

与えられた隣接行列のための有向プロップグラフを作成します。
