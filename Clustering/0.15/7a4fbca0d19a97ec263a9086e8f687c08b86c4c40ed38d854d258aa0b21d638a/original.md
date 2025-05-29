```
mcl(adj::AbstractMatrix; [kwargs...]) -> MCLResult
```

Perform MCL (Markov Cluster Algorithm) clustering using $n×n$ adjacency (points similarity) matrix `adj`.

# Arguments

Keyword arguments to control the MCL algorithm:

  * `add_loops::Bool` (enabled by default): whether the edges of weight 1.0 from the node to itself should be appended to the graph
  * `expansion::Number` (defaults to 2): MCL *expansion* constant
  * `inflation::Number` (defaults to 2): MCL *inflation* constant
  * `save_final_matrix::Bool` (disabled by default): whether to save the final equilibrium state in the `mcl_adj` field of the result; could provide useful diagnostic if the method doesn't converge
  * `prune_tol::Number`: pruning threshold
  * `display`, `maxiter`, `tol`: see [common options](@ref common_options)

# References

> Stijn van Dongen, *"Graph clustering by flow simulation"*, 2001


> [Original MCL implementation](http://micans.org/mcl).

