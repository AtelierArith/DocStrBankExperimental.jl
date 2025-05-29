```
dijkstra_shortest_paths(g, s, distmx=weights(g); allpaths=false)
dijkstra_shortest_paths(g, sources, distmx=weights(g); allpaths=false)
```

Performs [Dijkstra's algorithm](http://en.wikipedia.org/wiki/Dijkstra%27s_algorithm) on a graph, computing shortest distances between a source vertex `s` (or a vector `sources`)  and all other veritces. Returns a `DijkstraState` that contains various traversal information.

With `allpaths=true`, returns a `DijkstraState` that keeps track of all predecessors of a given vertex.
