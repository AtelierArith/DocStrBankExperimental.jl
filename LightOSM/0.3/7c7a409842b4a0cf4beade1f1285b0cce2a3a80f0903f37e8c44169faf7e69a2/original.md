```
restriction_cost_adjustment(g::OSMGraph)
```

Returns the cost adjustment function (user in dijkstra and astar) for restrictions. The return function  takes 3 arguments, `u` being the current node, `v` being the neighbour node, `parents` being the array  of parent dijkstra states. By default `g.indexed_restrictions` is used to check whether the path from  `u` to `v` is restricted given all previous nodes in `parents`.
