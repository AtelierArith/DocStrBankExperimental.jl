```
add_edge_dataset!(dg::D, edge_list, weight_list, attribute) where {D <: DataGraphUnion}
```

Add the edge data in `weight_list` to `dg`. `edge_list` is a list of edges (as node names, not integers) in `dg` and `weight_list` is a list of data/objects to be saved as edge data under the name `attribute`. `edge_list` and `weight_list` must have the same length, and entries of `weight_list` will be added to the corresponding edge in `edge_list`
