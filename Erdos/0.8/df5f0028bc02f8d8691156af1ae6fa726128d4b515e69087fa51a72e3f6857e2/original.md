```
bellman_ford_shortest_paths(g, s, distmx=weights(g))
bellman_ford_shortest_paths(g, sources, distmx=weights(g))
```

Uses the [Bellman-Ford algorithm](http://en.wikipedia.org/wiki/Bellman–Ford_algorithm) to compute shortest paths of all vertices of a `g` from a source vertex `s` (or a set of source vertices `sources`). Returns a `BellmanFordState` with relevant traversal information.
