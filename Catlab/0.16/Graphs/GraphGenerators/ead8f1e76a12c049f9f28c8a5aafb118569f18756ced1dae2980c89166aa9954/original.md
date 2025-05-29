```
watts_strogatz(n, k, β)
```

Return a [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) small world random graph with `n` vertices, each with expected degree `k` (or `k

  * 1`if`k`is odd). Edges are randomized per the model based on probability`β`.

The algorithm proceeds as follows. First, a perfect 1-lattice is constructed, where each vertex has exacly `div(k, 2)` neighbors on each side (i.e., `k` or `k - 1` in total). Then the following steps are repeated for a hop length `i` of `1` through `div(k, 2)`.

1. Consider each vertex `s` in turn, along with the edge to its `i`th nearest neighbor `t`, in a clockwise sense.
2. Generate a uniformly random number `r`. If `r ≥ β`, then the edge `(s, t)` is left unaltered. Otherwise, the edge is deleted and *rewired* so that `s` is connected to some vertex `d`, chosen uniformly at random from the entire graph, excluding `s` and its neighbors. (Note that `t` is a valid candidate.)

For `β = 0`, the graph will remain a 1-lattice, and for `β = 1`, all edges will be rewired randomly.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `seed=-1`: set the RNG seed.

### References

  * Collective dynamics of ‘small-world’ networks, Duncan J. Watts, Steven H. Strogatz. [https://doi.org/10.1038/30918](https://doi.org/10.1038/30918)
  * Small Worlds, Duncan J. watts. [https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416](https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416)
  * https://github.com/JuliaGraphs/LightGraphs.jl/blob/2a644c2b15b444e7f32f73021ec276aa9fc8ba30/src/SimpleGraphs/generators/randgraphs.jl#L187
