```
construct_matrix_from_eigen(
    eigenvalues::Vector{<:Real},
    eigenvectors::Matrix{<:Real},
)
```

Constructs a matrix from its eigenvalue decomposition.

### Inputs

  * `eigenvalues` - A vector of eigenvalues.
  * `eigenvectors` - A matrix of eigenvectors. The i'th column corresponds to the i'th eigenvalue.

### Returns

  * A `Matrix`.
