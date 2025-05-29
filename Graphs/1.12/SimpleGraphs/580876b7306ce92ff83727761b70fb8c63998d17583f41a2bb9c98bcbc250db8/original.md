```
newman_watts_strogatz(n, k, β)
```

Return a Newman-Watts-Strogatz small world random graph with `n` vertices, each with expected degree `k(1 + β)` (or `(k - 1)(1 + β)` if `k` is odd). Edges are randomized per the model based on probability `β`.

The algorithm proceeds as follows. First, a perfect 1-lattice is constructed, where each vertex has exacly `div(k, 2)` neighbors on each side (i.e., `k` or `k - 1` in total). Then the following steps are repeated for a hop length `i` of `1` through `div(k, 2)`.

1. Consider each vertex `s` in turn, along with the edge to its `i`th nearest neighbor `t`, in a clockwise sense.
2. Generate a uniformly random number `r`. If `r < β`, `s` is connected to some vertex `d`, chosen uniformly at random from the entire graph, excluding `s` and its neighbors. (Note that `t` is a valid candidate.)

For `β = 0`, the graph will remain a 1-lattice, and for `β = 1`, all edges will be rewired randomly.

Note: In the original paper by Newman and Watts, self-loops and double edges were allowed, which is not the case here. However, for large enough networks and small enough `p` and `k`, this should not deviate much from the original model.

### Optional Arguments

  * `is_directed=false`: if true, return a directed graph.
  * `rng=nothing`: set the Random Number Generator.
  * `seed=nothing`: set the RNG seed.

## Examples

`````
julia> using Graphs

julia> newman_watts_strogatz(10, 4, 0.3)
{10, 26} undirected simple Int64 graph
````
`````

jldoctest

julia> newman*watts*strogatz(Int8(10), 4, 0.8, is_directed=true, seed=123) {10, 36} directed simple Int8 graph ```

### References

  * Scaling and percolation in the small-world network model, M. E. J. Newman, Duncan J. Watts. [https://doi.org/10.1103/PhysRevE.60.7332](https://doi.org/10.1103/PhysRevE.60.7332)
