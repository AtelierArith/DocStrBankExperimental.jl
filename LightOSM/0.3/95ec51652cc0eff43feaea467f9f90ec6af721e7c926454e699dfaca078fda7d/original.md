```
time_heuristic(g::OSMGraph)
```

Returns the heuristic function used in astar shortest path calculation, should be used with a graph with `weight_type=:time` or `weight_type=:lane_efficiency`. The heuristic function takes in 2 arguments, `u`  being the current node and `v` being the neighbour node, and returns the estimated travel time between them.  Calculated by dividing the harversine distance by a fixed maxspeed of `100`. Remember to achieve an optimal path, it is important to pick an *underestimating* heuristic that best estimates the cost remaining to the `goal`, hence we pick the largest maxspeed across all ways.
