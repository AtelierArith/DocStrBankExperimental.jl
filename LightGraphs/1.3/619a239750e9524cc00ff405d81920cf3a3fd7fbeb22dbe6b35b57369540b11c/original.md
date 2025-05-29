```
a_star(g, s, t[, distmx][, heuristic])
```

Return a vector of edges comprising the shortest path between vertices `s` and `t` using the [A* search algorithm](http://en.wikipedia.org/wiki/A%2A_search_algorithm). An optional heuristic function and edge distance matrix may be supplied. If missing, the distance matrix is set to [`LightGraphs.DefaultDistance`](@ref) and the heuristic is set to `n -> 0`.
