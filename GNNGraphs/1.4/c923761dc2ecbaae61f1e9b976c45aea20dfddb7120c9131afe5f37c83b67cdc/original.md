```
edge_type_subgraph(g::GNNHeteroGraph, edge_ts)
```

Return a subgraph of `g` that contains only the edges of type `edge_ts`. Edge types can be specified as a single edge type (i.e. a tuple containing 3 symbols) or a vector of edge types.
