```julia
eigen_decomp(H, s; lvl, kwargs...)

```

Calculate the eigen value decomposition of the Hamiltonian `H` at an array of  time points `s`. The output keeps the lowest `lvl` eigenstates and their  corresponding eigenvalues. Output `(vals, vecs)` have the dimensions of  `(lvl, length(s))` and `(size(H, 1), lvl, length(s))` respectively.
