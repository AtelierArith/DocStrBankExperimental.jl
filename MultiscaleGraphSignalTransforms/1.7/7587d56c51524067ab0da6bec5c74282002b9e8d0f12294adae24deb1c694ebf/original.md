```
standardize_eigenvectors!(𝚽::Matrix{Float64})
```

standardize the signs of the eigenvectors such that 1) the term with the largest magnitude is positive; 2) if the max == -min, then make sure the first non-zero entry of the eigenvector is positive.

# Input Arguments

  * `𝚽::Matrix{Float64}`: matrix of graph Laplacian eigenvectors
