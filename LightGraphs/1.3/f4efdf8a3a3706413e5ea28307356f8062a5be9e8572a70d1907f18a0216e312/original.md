```
floyd_warshall_shortest_paths(g, distmx=weights(g))
```

Use the [Floyd-Warshall algorithm](http://en.wikipedia.org/wiki/Floyd–Warshall_algorithm) to compute the shortest paths between all pairs of vertices in graph `g` using an optional distance matrix `distmx`. Return a [`LightGraphs.FloydWarshallState`](@ref) with relevant traversal information.

### Performance

Space complexity is on the order of $\mathcal{O}(|V|^2)$.
