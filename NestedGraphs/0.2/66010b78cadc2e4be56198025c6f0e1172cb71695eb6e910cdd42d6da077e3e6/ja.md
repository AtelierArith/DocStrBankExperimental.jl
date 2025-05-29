```julia
subgraphedge(
    ng::NestedGraphs.NestedGraph,
    e::Graphs.SimpleGraphs.SimpleEdge
) -> Union{Nothing, Graphs.SimpleGraphs.SimpleEdge}

```

エッジの部分グラフを取得します。エッジが2つの部分グラフを接続している場合、`nothing`を返します。
