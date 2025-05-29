```
get_path(datagraph, src_node, intermediate_node, dst_node; algorithm = "Dijkstra")
```

Returns the shortest path in the `datagraph` between `src_node` and `dst_node` which passes through `intermediate node`.

`algorithm` is a string key word. Options are limited to "Dijkstra", "BellmanFord"
