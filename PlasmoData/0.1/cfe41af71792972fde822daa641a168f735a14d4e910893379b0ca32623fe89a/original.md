```
add_node_dataset!(dg::D, weight_dict, attribute) where {D <: DataGraphUnion}
```

Add the data in `weight_dict` as node data on `dg` under the name `attribute`. `weight_dict` must contain keys that correspond to the node names in `dg.nodes`.
