```julia
static_simple_graph(
    A::Matrix{Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.StaticType, EasyABM.SimGType}}

```

与えられた隣接行列のための単純なプロップグラフを作成します。
