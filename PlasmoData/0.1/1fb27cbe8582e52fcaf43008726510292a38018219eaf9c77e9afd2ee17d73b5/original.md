```
get_path(datagraph, src_node, dst_node; algorithm = "Dijkstra")
```

Returns the shortest path in the `datagraph` between `src_node` and `dst_node`. Shortest path is computed by Dijkstra's algorithm

`algorithm` is a string key word. Options are limited to "Dijkstra", "BellmanFord"
