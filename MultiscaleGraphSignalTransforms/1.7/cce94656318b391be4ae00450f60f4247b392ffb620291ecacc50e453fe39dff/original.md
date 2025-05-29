```
nat_spec_filter(l, D; σ = 0.25 * maximum(D), method = :regular, thres = 0.2)
```

assemble the natural spectral graph filter centered at the l-th eigenvector via the distance matrix `D`.

# Input Arguments

  * `l::Int64`: index of the centered eigenvector
  * `D::Matrix{Float64}`: non-trivial distance matrix of the eigenvectors
  * `σ::Float64`: Gaussian window width parameter (default: `0.25 * maximum(D)`)
  * `method::Symbol`: `:regular` or `:reduced` (default: `:regular`)
  * `thres::Float64`: cutoff threshold ∈ (0, 1).

# Output Argument

  * `𝛍::Vector{Float64}`: the natural spectral graph filter
