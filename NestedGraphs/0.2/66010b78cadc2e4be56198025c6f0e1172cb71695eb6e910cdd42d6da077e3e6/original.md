```julia
subgraphedge(
    ng::NestedGraphs.NestedGraph,
    e::Graphs.SimpleGraphs.SimpleEdge
) -> Union{Nothing, Graphs.SimpleGraphs.SimpleEdge}

```

Get the subgraph of an edge If the edge connects 2 subgraphs, it returns `nothing`
