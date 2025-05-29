```julia
dynamic_simple_graph(
    g::Graphs.SimpleGraphs.SimpleGraph{Int64}
) -> Union{Nothing, EasyABM.SimplePropGraph{EasyABM.MortalType, EasyABM.SimGType}}

```

与えられた Graphs.jl で作成された単純グラフから単純なプロップグラフを作成します。
