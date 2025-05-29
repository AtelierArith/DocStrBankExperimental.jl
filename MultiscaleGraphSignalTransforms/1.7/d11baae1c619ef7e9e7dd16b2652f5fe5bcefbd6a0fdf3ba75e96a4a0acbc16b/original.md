```
eigsROT_Distance(P::Matrix{Float64}, W::SparseMatrixCSC{Float64, Int64}, X::Matrix{Float64}; α::Float64 = 1.0)
```

computes the sROT distance matrix of P's column vectors on a (unweighted) tree.

# Input Argument

  * `P::Matrix{Float64}`: a matrix whose columns are vector measures with the same total mass.
  * `W::SparseMatrixCSC{Float64, Int64}`: the weight matrix of the tree.
  * `X::Matrix{Float64}`: the node positions (i-th row represents node `i`'s location)
  * `α::Float64`: default is 1.0. ROT parameter.

# Output Argument

  * `dist_sROT::Matrix{Float64}`: distance matrix, dist*sROT[i,j] = d*{sROT}(pᵢ, pⱼ; α).
  * `Ws::SparseMatrixCSC{Float64, Int64}`: the weight matrix of the simplified tree.
  * `Xs::Matrix{Float64}`: the node locations of the simplified tree
  * `𝚯::Matrix{Float64}`: the shortened pmfs from `P`.
