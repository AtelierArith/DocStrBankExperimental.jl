```
floyd_warshall_shortest_paths(g, distmx=weights(g))
```

Use the [Floyd-Warshall algorithm](http://en.wikipedia.org/wiki/Floyd–Warshall_algorithm) to compute the shortest paths between all pairs of vertices in graph `g` using an optional distance matrix `distmx`. Return a [`Graphs.FloydWarshallState`](@ref) with relevant traversal information (try querying `state.parents` or `state.dists`).

### Performance

Space complexity is on the order of `O(|V|^2)`.
