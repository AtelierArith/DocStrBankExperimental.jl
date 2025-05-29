```
MCLResult <: ClusteringResult
```

The output of [`mcl`](@ref) function.

# Fields

  * `mcl_adj::AbstractMatrix`: the final MCL adjacency matrix (equilibrium state matrix if the algorithm converged), empty if `save_final_matrix` option is disabled
  * `assignments::Vector{Int}`: indices of the points clusters. `assignments[i]` is the index of the cluster for the $i$-th point  ($0$ if unassigned)
  * `counts::Vector{Int}`: the $k$-length vector of cluster sizes
  * `nunassigned::Int`: the number of standalone points not assigned to any cluster
  * `iterations::Int`: the number of elapsed iterations
  * `rel_Δ::Float64`: the final relative Δ
  * `converged::Bool`: whether the method converged
