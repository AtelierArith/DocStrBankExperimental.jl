```
add_self_loops(g::GNNHeteroGraph, edge_t::EType)
add_self_loops(g::GNNHeteroGraph)
```

If the source node type is the same as the destination node type in `edge_t`, return a graph with the same features as `g` but also add self-loops  of the specified type, `edge_t`. Otherwise, it returns `g` unchanged.

Nodes with already existing self-loops of type `edge_t` will obtain  a second set of self-loops of the same type.

If the graph has edge weights for edges of type `edge_t`, the new edges will have weight 1.

If no edges of type `edge_t` exist, or all existing edges have no weight,  then all new self loops will have no weight.

If `edge_t` is not passed as argument, for the entire graph self-loop is added to each node for every edge type in the graph where the source and destination node types are the same.  This iterates over all edge types present in the graph, applying the self-loop addition logic to each applicable edge type.
