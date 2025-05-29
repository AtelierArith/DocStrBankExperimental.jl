```julia
getmlsquashedgraph(
    ng::NestedGraphs.NestedGraph
) -> Tuple{Graphs.AbstractGraph{T} where T<:Integer, Any}

```

マルチレイヤーグラフを圧縮して取得します。すべてのマルチレイヤー頂点は単一の頂点に圧縮されます。すべての層のすべてのエッジが統合されます。
