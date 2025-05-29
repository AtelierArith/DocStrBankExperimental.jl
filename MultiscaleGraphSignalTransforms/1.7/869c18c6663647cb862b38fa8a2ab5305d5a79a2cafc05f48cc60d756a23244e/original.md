```
eigHAD_Affinity(𝚽, 𝛌; indexEigs = 1:size(𝚽,2))
```

EIGHAD_AFFINITY compute Hadamard (HAD) affinity between pairwise graph Laplacian eigenvectors.

# Input Arguments

  * `𝚽::Matrix{Float64}`: matrix of graph Laplacian eigenvectors, 𝜙ⱼ₋₁ (j = 1,...,size(𝚽,1)).
  * `𝛌::Array{Float64}`: array of eigenvalues. (ascending order)
  * `indexEigs::Int`: default is all eigenvectors, indices of eigenvectors considered.

# Output Argument

  * `A::Matrix{Float64}`: a numEigs x numEigs affinity matrix, A[i,j] = a_HAD(𝜙ᵢ₋₁, 𝜙ⱼ₋₁).
