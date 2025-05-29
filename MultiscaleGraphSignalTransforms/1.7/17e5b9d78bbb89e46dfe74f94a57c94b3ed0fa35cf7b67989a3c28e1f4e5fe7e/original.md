```
ROT_Distance(A, B, Q; edge_length = 1, α = 1.0)
```

computes the ROT distance matrix from A's column vectors to B's column vectors. If A, B are vector inputs, then it also returns the cost value and the optimal transport plan.

# Input Argument

  * `A::Any`: a vector or matrix whose columns are initial probability measures.
  * `B::Any`: a vector or matrix whose columns are terminal probability measures.
  * `Q::SparseMatrixCSC{Int64,Int64}`: the unweighted incidence matrix of the graph.
  * `edge_length::Any`: the length vector (default: `1` represents unweighted graphs)
  * `α::Float64`: default is `1.0`. ROT parameter.
  * `retPlan::Bool`: an indicator if return the optimal plan (default: `false`)

# Output Argument

  * `dis::Matrix{Float64}`: distance matrix, dis[i,j] = d_{ROT}(aᵢ, bⱼ; α).
