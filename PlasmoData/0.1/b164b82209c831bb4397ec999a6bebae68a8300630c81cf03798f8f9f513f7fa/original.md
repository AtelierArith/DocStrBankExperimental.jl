```
add_edge_data!(datadigraph, node_name1, node_name2, edge_weight, attribute_name)
add_edge_data!(datadigraph, edge, edge_weight, attribute_name)
```

Add a weight value for the edge between node*name1 and node*name2 in the DataDiGraph object. When using the second function, `edge` must be a tuple with two node names. User must pass an "attribute name" for the given weight. All other edges that do not have an edge_weight value defined for that attribute name default to a value of zero.
