```
eigTSD_Distance(P::Matrix{Float64}, 𝚽::Matrix{Float64}, 𝛌::Vector{Float64},
                Q::SparseMatrixCSC{Int64,Int64}; length::Any = 1,
                T::Any = :Inf, tol::Float64 = 1e-5)
```

computes the TSD distance matrix of P's column vectors on a graph.

# Input Argument

  * `P::Matrix{Float64}`: vector measures with the same total mass 0.
  * `𝚽::Matrix{Float64}`: matrix of the unweighted graph Laplacian eigenvectors.
  * `𝛌::Vector{Float64}`: vector of eigenvalues.
  * `Q::SparseMatrixCSC{Int64,Int64}`: the unweighted incidence matrix.
  * `length::Any`: vector of edge lengths (default: `1` represents unweighted graphs)
  * `T::Any`: the stopping time T in K_functional (default: `:Inf`)
  * `tol::Float64`: tolerance for integral convergence (default: `1e-5`)

# Output Argument

  * `dis::Matrix{Float64}`: distance matrix, d_{TSD}(φᵢ, φⱼ; T).
