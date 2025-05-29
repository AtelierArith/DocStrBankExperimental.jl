```
floyd_warshall_shortest_paths(g, distmx=weights(g))
```

Uses the [Floyd-Warshall algorithm](http://en.wikipedia.org/wiki/Floyd–Warshall_algorithm) to compute shortest paths between all pairs of vertices in graph `g`. Returns a `FloydWarshallState` with relevant traversal information, each is a vertex-indexed vector of vectors containing the metric for each vertex in the graph.

Note that this algorithm may return a large amount of data (it will allocate on the order of $O(nv^2)$).
