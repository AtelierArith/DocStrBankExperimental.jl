```
add_edge_dataset!(dg::D, weight_dict, attribute) where {D <: DataGraphUnion}
```

Add the data in `weight_dict` as edge data on `dg` under the name `attribute`. `weight_dict` must contain keys that correspond to the edges (as node names, not integers) in `dg.edges`.
