```
FuzzyCMeansResult{T<:AbstractFloat}
```

The output of [`fuzzy_cmeans`](@ref) function.

# Fields

  * `centers::Matrix{T}`: the $d×C$ matrix with columns being the centers of resulting fuzzy clusters
  * `weights::Matrix{Float64}`: the $n×C$ matrix of assignment weights ($\mathrm{weights}_{ij}$ is the weight (probability) of assigning $i$-th point to the $j$-th cluster)
  * `iterations::Int`: the number of executed algorithm iterations
  * `converged::Bool`: whether the procedure converged
