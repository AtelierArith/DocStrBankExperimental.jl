```julia
getmlsquashedgraph(
    ng::NestedGraphs.NestedGraph
) -> Tuple{Graphs.AbstractGraph{T} where T<:Integer, Any}

```

Get a squashed multilayer graph. All multilayer vertices are squashed down to a single vertex. All edges in all layers are merged.
