```
edge_index(g::GNNHeteroGraph, [edge_t])
```

Return a tuple containing two vectors, respectively storing the source and target nodes for each edges in `g` of type `edge_t = (src_t, rel_t, trg_t)`.

If `edge_t` is not provided, it will error if `g` has more than one edge type.
