```julia
eigen_decomp(H, t; lvl, kwargs...)

```

Calculate the eigen value decomposition of the Hamiltonian `H` at time `t`.  Keyword argument `lvl` specifies the number of levels to keep in the output.  `w` is a vector of eigenvalues and `v` is a matrix of the eigenvectors in the  columns. (The `k`th eigenvector can be obtained from the slice `v[:, k]`.) `w`  will be in unit of `GHz`.
