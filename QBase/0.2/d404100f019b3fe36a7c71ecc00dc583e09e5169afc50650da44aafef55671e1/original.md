```
von_neumann_entropy( ρ :: AbstractMatrix ) :: Float64
```

The von neumann entropy of a density matrix:

$$
S(\rho) = - \sum_j  \lambda_j \log_2(\lambda_j)
$$

where $\lambda_j$ are the eigenvalues of quantum  state $\rho$.

A `DomainError` is thrown if `ρ` does not satisfy [`is_density_matrix`](@ref).
