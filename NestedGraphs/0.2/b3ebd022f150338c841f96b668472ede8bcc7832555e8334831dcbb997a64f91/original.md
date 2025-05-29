```julia
getallsubgraphpaths(
    ng::NestedGraphs.NestedGraph;
    startingpath
) -> Union{Nothing, Vector{Vector{Int64}}}

```

Get all id path that lead to a subgraph, starting with `startingpath`. If no `startingpath` is given, search all subgraphs.
