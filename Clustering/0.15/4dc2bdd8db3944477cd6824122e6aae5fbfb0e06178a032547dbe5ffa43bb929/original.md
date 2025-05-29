```
KmedoidsResult{T} <: ClusteringResult
```

The output of [`kmedoids`](@ref) function.

# Fields

  * `medoids::Vector{Int}`: the indices of $k$ medoids
  * `assignments::Vector{Int}`: the indices of clusters the points are assigned to, so that `medoids[assignments[i]]` is the index of the medoid for the $i$-th point
  * `costs::Vector{T}`: assignment costs, i.e. `costs[i]` is the cost of assigning $i$-th point to its medoid
  * `counts::Vector{Int}`: cluster sizes
  * `totalcost::Float64`: total assignment cost (the sum of `costs`)
  * `iterations::Int`: the number of executed algorithm iterations
  * `converged::Bool`: whether the procedure converged
