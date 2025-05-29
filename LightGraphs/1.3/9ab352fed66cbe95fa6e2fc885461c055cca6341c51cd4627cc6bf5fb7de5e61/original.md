```
johnson_shortest_paths(g, distmx=weights(g))
```

Use the [Johnson algorithm](https://en.wikipedia.org/wiki/Johnson%27s_algorithm) to compute the shortest paths between all pairs of vertices in graph `g` using an optional distance matrix `distmx`.

Return a [`LightGraphs.JohnsonState`](@ref) with relevant traversal information.

### Performance

Complexity: O(|V|*|E|)
