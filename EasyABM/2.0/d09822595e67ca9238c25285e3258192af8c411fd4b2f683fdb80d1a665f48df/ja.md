```julia
static_simple_graph(
    structure::Dict{Int64, Vector{Int64}}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.StaticType, EasyABM.SimGType}}

```

与えられた構造を持つ単純なプロップグラフを作成します。
