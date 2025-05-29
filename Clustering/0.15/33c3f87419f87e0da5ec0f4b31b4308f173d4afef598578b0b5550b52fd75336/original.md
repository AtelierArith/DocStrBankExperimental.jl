```
AffinityPropResult <: ClusteringResult
```

The output of affinity propagation clustering ([`affinityprop`](@ref)).

# Fields

  * `exemplars::Vector{Int}`: indices of *exemplars* (cluster centers)
  * `assignments::Vector{Int}`: cluster assignments for each data point
  * `iterations::Int`: number of iterations executed
  * `converged::Bool`: converged or not
