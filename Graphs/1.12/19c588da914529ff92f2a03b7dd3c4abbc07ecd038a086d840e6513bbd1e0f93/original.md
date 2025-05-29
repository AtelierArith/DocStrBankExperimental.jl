```
kruskal_mst(g, distmx=weights(g); minimize=true)
```

Return a vector of edges representing the minimum (by default) spanning tree of a connected,  undirected graph `g` with optional distance matrix `distmx` using [Kruskal's algorithm](https://en.wikipedia.org/wiki/Kruskal%27s_algorithm).

### Optional Arguments

  * `minimize=true`: if set to `false`, calculate the maximum spanning tree.
