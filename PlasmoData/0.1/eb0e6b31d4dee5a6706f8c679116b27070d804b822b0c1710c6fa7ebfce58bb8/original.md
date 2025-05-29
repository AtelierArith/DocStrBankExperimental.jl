```
add_node_dataset!(dg::D, weight_list, attribute) where {D <: DataGraphUnion}
```

Add the entries of `weight_list` as node data on `dg` under the name `attribute`. `weight_list` must be the same length as the number of nodes in `dg`. Entries of `weight_list` will be added as node data in the order that nodes are listed in `dg.nodes`.
