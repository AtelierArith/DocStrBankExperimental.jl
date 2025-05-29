```
add_edge_dataset!(dg::D, weight_list, attribute) where {D <: DataGraphUnion}
```

Add the entries of `weight_list` as edge data on `dg` under the name `attribute`. `weight_list` must be the same length as the number of edges in `dg`. Entries of `weight_list` will be added as edge data in the order that edges are listed in `dg.edges`.
