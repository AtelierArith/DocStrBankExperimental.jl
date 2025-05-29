```
eigROT_Distance(P, Q; edge_length = 1, α = 1.0)
```

computes the ROT distance matrix of P's column vectors on a graph.

# Input Argument

  * `P::Matrix{Float64}`: a matrix whose columns are vector measures with the same total mass.
  * `Q::SparseMatrixCSC{Int64,Int64}`: the unweighted incidence matrix of the graph.
  * `edge_length::Any`: the length vector (default: 1 represents unweighted graphs)
  * `α::Float64`: default is 1.0. ROT parameter.

# Output Argument

  * `dis::Matrix{Float64}`: distance matrix, dis[i,j] = d_{ROT}(pᵢ, pⱼ; α).
