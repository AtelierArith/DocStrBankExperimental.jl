```
boruvka_mst(g, distmx = weights(g); minimize = true)
```

Return a tuple `(mst, weights)` where `mst` is a vector of edges representing the optimum (minimum, by default) spanning tree of a connected, undirected graph `g` with optional matrix `distmx` that provides distinct edge weights, and `weights` is the sum of all the edges in the solution by using [Boruvka's algorithm](https://en.wikipedia.org/wiki/Bor%C5%AFvka%27s_algorithm). The algorithm requires that all edges have different weights to correctly generate a minimun/maximum spanning tree

### Optional Arguments

  * `minimize=true`: if set to `false`, calculate the maximum spanning tree.
