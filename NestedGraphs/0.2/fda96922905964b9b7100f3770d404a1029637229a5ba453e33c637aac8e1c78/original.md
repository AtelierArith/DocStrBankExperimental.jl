```julia
getmlvertices(
    ng::NestedGraphs.NestedGraph;
    subgraph_view
) -> Any

```

Get all multilayer vertices. Each multilayer vertex is composed by vertices of the graph that are connected and in different layers. In other words, return all nodes of `ng` that are connected through the interlinks, i.e., the NestedEdges, i.e., the edges connecting different layers, i.e., the edges connecting different subgraphs. Malfunctions if more nodes across layers are connected with several non-vertical ways.
