```
a_star(g, s, t, distmx=weights(g), heuristic = n->0)
```

Computes the shortest path between vertices `s` and `t` using the [A* search algorithm](http://en.wikipedia.org/wiki/A%2A_search_algorithm). An optional heuristic function and edge distance matrix may be supplied. Returns an empty path if there are no such paths.
