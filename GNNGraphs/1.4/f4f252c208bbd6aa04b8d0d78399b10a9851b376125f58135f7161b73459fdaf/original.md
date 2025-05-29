```
add_edges(g::GNNHeteroGraph, edge_t, s, t; [edata, num_nodes])
add_edges(g::GNNHeteroGraph, edge_t => (s, t); [edata, num_nodes])
add_edges(g::GNNHeteroGraph, edge_t => (s, t, w); [edata, num_nodes])
```

Add to heterograph `g` edges of type `edge_t` with source node vector `s` and target node vector `t`. Optionally, pass the  edge weights `w` or the features  `edata` for the new edges. `edge_t` is a triplet of symbols `(src_t, rel_t, dst_t)`. 

If the edge type is not already present in the graph, it is added.  If it involves new node types, they are added to the graph as well. In this case, a dictionary or named tuple of `num_nodes` can be passed to specify the number of nodes of the new types, otherwise the number of nodes is inferred from the maximum node id in `s` and `t`.
