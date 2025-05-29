```julia
getsquashedgraph(
    ng::NestedGraphs.NestedGraph{T, R, N},
    sqvertices::Array{Array{Q<:Integer, 1}, 1}
) -> Tuple{Any, Any}

```

`sqvertices` は `ng` の `flatgr` に統合/圧縮されるノードです。また、`ng` の頂点をグラフの新しい頂点にマッピングするものも返します。本質的には、`Graphs.merge_vertices` を再帰的に呼び出します。
