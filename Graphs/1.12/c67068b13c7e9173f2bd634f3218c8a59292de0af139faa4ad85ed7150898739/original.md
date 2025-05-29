```
bellman_ford_shortest_paths(g, s, distmx=weights(g))
bellman_ford_shortest_paths(g, ss, distmx=weights(g))
```

Compute shortest paths between a source `s` (or list of sources `ss`) and all other nodes in graph `g` using the [Bellman-Ford algorithm](http://en.wikipedia.org/wiki/Bellman–Ford_algorithm).

Return a [`Graphs.BellmanFordState`](@ref) with relevant traversal information (try querying `state.parents` or `state.dists`).
