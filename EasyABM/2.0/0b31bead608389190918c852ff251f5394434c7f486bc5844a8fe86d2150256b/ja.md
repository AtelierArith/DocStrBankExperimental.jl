```julia
dynamic_dir_graph(
    g::Graphs.SimpleGraphs.SimpleDiGraph{Int64}
) -> Union{Nothing, EasyABM.DirPropGraph{EasyABM.MortalType, EasyABM.DirGType}}

```

指定された有向グラフ（Graphs.jlで作成された）に対して、有向プロップグラフを作成します。
