```julia
getfoldedgraph(
    ng::NestedGraphs.NestedGraph,
    subgrpaths::Array{Array{T<:Integer, 1}, 1}
) -> Tuple{Graphs.AbstractGraph{T} where T<:Integer, Any}

```

Get flat graph by substituting graphs identified with `subgrpaths` with nodes. Return also a mapping.
