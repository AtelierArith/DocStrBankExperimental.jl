```
add_node_dataset!(dg::D, node_list, weight_list, attribute) where {D <: DataGraphUnion}
```

Add the node data in `weight_list` to `dg`. `node_list` is a list of nodes in `dg` and `weight_list` is a list of values/things to be saved as node data under the name `attribute`. `node_list` and `weight_list` must have the same length, and entries of `weight_list` will be added to the corresponding node in `node_list`
