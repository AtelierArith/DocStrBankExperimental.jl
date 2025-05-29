```
G, vert_map = region_adjacency_graph(seg, weight_fn)
```

Constructs a region adjacency graph (RAG) from the `SegmentedImage`. It returns the RAG along with a Dict(label=>vertex) map. `weight_fn` is used to assign weights to the edges.

```
weight_fn(label1, label2)
```

Returns a real number corresponding to the weight of the edge between label1 and label2.
