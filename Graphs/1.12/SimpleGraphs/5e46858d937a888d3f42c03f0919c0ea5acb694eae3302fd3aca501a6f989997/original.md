```
watts_strogatz(n, k, β)
```

Return a [Watts-Strogatz](https://en.wikipedia.org/wiki/Watts_and_Strogatz_model) small world random graph with `n` vertices, each with expected degree `k`  (or `k - 1` if `k` is odd). Edges are randomized per the model based on probability `β`.

The algorithm proceeds as follows. First, a perfect 1-lattice is constructed, where each vertex has exacly `div(k, 2)` neighbors on each side (i.e., `k` or `k - 1` in total). Then the following steps are repeated for a hop length `i` of `1` through `div(k, 2)`.

1. Consider each vertex `s` in turn, along with the edge to its `i`th nearest neighbor `t`, in a clockwise sense.
2. Generate a uniformly random number `r`. If `r ≥ β`, then the edge `(s, t)` is left unaltered. Otherwise, the edge is deleted and *rewired* so that `s` is connected to some vertex `d`, chosen uniformly at random from the entire graph, excluding `s` and its neighbors. (Note that `t` is a valid candidate.)

For `β = 0`, the graph will remain a 1-lattice, and for `β = 1`, all edges will be rewired randomly.

### Optional Arguments

  * `remove_edges=true`: if false, do not remove the original edges.
  * `is_directed=false`: if true, return a directed graph.
  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

## Examples

```jldoctest
julia> using Graphs

julia> watts_strogatz(10, 4, 0.3)
{10, 20} undirected simple Int64 graph

julia> watts_strogatz(Int8(10), 4, 0.8, is_directed=true, seed=123)
{10, 20} directed simple Int8 graph
```

### References

  * Collective dynamics of ‘small-world’ networks, Duncan J. Watts, Steven H. Strogatz. [https://doi.org/10.1038/30918](https://doi.org/10.1038/30918)
  * Small Worlds, Duncan J. watts. [https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416](https://en.wikipedia.org/wiki/Special:BookSources?isbn=978-0691005416)
