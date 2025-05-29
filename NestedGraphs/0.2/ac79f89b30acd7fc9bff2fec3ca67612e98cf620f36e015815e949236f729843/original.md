```julia
getsquashedgraph(
    ng::NestedGraphs.NestedGraph{T, R, N},
    sqvertices::Array{Array{Q<:Integer, 1}, 1}
) -> Tuple{Any, Any}

```

`sqvertices` are the nodes to be merged/squashed together to the `flatgr` of `ng`. Return also a mapping of the `ng` vertices to the new vertices of the graph. Essentially it recursively calls `Graphs.merge_vertices`.
