```
johnson_shortest_paths(g, distmx=weights(g))
```

Use the [Johnson algorithm](https://en.wikipedia.org/wiki/Johnson%27s_algorithm) to compute the shortest paths between all pairs of vertices in graph `g` using an optional distance matrix `distmx`.

Return a [`Graphs.JohnsonState`](@ref) with relevant traversal information (try querying `state.parents` or `state.dists`).

### Performance

Complexity: `O(|V|*|E|)`
