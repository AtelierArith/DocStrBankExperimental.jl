```
add_edge_attribute!(datagraph, attribute, default_weight = 0.0)
add_edge_attribute!(datadigraph, attribute, default_weight = 0.0)
```

Add a column filled with `default_weight` to the `edge_data` matrix with the name `attribute`. If `attribute` already exists in the edge data, an error is thrown.
