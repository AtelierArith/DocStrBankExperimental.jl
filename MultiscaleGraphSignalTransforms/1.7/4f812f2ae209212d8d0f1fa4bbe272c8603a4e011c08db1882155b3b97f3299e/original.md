```
K_functional(𝐩::Vector{Float64}, 𝐪::Vector{Float64}, 𝚽::Matrix{Float64},
             ∇𝚽::Matrix{Float64}, 𝛌::Vector{Float64}; length::Any = 1,
             T::Any = :Inf, dt::Float64 = 0.5/maximum(𝛌), tol::Float64 = 1e-5)
```

computes the K_functional between two vector meassures 𝐩 and 𝐪 on a graph.

# Input Argument

  * `𝐩::Vector{Float64}`: the source vector measure.
  * `𝐪::Vector{Float64}`: the destination vector measure.
  * `𝚽::Matrix{Float64}`: matrix of the unweighted graph Laplacian eigenvectors.
  * `∇𝚽::Matrix{Float64}`: gradient of unweighted graph Laplacian eigenvectors.
  * `𝛌::Vector{Float64}`: vector of eigenvalues.
  * `length::Any`: vector of edge lengths (default: 1 represents unweighted graphs)
  * `T::Any`: the stopping time T in K_functional (default: :Inf)
  * `tol::Float64`: tolerance for convergence (default: 1e-5)

# Output Argument

  * `K::Float64`: TSD distance d_{TSD}(p, q; T).
  * `E::Float64`: an estimated upper bound on the absolute error. In general,   `E <= tol * norm(K)`.
