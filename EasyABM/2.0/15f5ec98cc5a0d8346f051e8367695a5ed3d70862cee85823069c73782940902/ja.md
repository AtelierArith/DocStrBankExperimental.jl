```julia
static_dir_graph(
    in_structure::Dict{Int64, Vector{Int64}}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.StaticType, EasyABM.DirGType}}

```

与えられた構造を持つ有向プロップグラフを作成します。
