```
ngwf_all_vectors(D, 𝚽; σ = 0.2 * maximum(D))
```

assemble the whole NGWF dictionary.

# Input Arguments

  * `D::Matrix{Float64}`: non-trivial distance matrix of the eigenvectors
  * `𝚽::Matrix{Float64}`: graph Laplacian eigenvectors
  * `σ::Float64`: Gaussian window width parameter (default: `0.25 * maximum(D)`)

# Output Argument

  * `𝓤::Matrix{Float64}`: the NGWF dictionary
