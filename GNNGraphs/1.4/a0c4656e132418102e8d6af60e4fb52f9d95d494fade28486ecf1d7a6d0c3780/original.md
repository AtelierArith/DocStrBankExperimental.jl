```
graph_indicator(g::GNNHeteroGraph, [node_t])
```

Return a Dict of vectors containing the graph membership (an integer from `1` to `g.num_graphs`) of each node in the graph for each node type. If `node_t` is provided, return the graph membership of each node of type `node_t` instead.

See also [`batch`](@ref).
