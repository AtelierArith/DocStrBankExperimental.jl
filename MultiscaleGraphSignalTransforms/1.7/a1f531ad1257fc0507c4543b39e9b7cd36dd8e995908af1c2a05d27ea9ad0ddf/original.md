```
eigHAD_Distance(𝚽, 𝛌; indexEigs = 1:size(𝚽,2))
```

compute HAD "distance" (not really a distance) between pairwise graph Laplacian eigenvectors, i.e., d*HAD(𝜙ᵢ₋₁, 𝜙ⱼ₋₁) = √(1 - a*HAD(𝜙ᵢ₋₁, 𝜙ⱼ₋₁)²).

# Input Arguments

  * `𝚽::Matrix{Float64}`: matrix of graph Laplacian eigenvectors, 𝜙ⱼ₋₁ (j = 1,...,size(𝚽,1)).
  * `𝛌::Array{Float64}`: array of eigenvalues. (ascending order)
  * `indexEigs::Int`: default is all eigenvectors, indices of eigenvectors considered.

# Output Argument

  * `dis::Matrix{Float64}`: the HAD distance matrix, dis[i,j] = d_HAD(𝜙ᵢ₋₁, 𝜙ⱼ₋₁).
