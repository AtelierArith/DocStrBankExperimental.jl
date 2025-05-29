```
rngwf_all_vectors(D, 𝚽; σ = 0.2 * maximum(D), thres = 0.2)
```

assemble the reduced NGWF (rNGWF) dictionary.

# Input Arguments

  * `D::Matrix{Float64}`: non-trivial distance matrix of the eigenvectors
  * `𝚽::Matrix{Float64}`: graph Laplacian eigenvectors
  * `σ::Float64`: Gaussian window width parameter (default: `0.25 * maximum(D)`)
  * `thres::Float64`: cutoff threshold ∈ (0, 1).

# Output Argument

  * `𝓤::Matrix{Float64}`: the rNGWF dictionary
  * `dic_l2x::Dict`: a dictionary to store the filtered locations by QR at the l-th   centered eigenvector
