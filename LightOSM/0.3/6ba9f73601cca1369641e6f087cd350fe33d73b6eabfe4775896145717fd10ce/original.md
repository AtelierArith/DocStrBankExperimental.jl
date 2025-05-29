```
distance_heuristic(g::OSMGraph)
```

Returns the heuristic function used in astar shortest path calculation, should be used with a graph with `weight_type=:distance`. The heuristic function takes in 2 arguments, `u` being the current node and `v`  being the neighbour node, and returns the haversine distance between them.
