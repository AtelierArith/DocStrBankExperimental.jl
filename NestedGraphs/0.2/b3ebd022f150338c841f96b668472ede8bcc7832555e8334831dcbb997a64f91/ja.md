```julia
getallsubgraphpaths(
    ng::NestedGraphs.NestedGraph;
    startingpath
) -> Union{Nothing, Vector{Vector{Int64}}}

```

サブグラフに至るすべてのIDパスを取得します。`startingpath` から始まります。`startingpath` が指定されていない場合は、すべてのサブグラフを検索します。
