```
gram_matrix(g::HermLocalGenus, i::Int) -> MatElem
```

Given a local genus symbol `g` for hermitian lattices over $E/K$ at a prime ideal $\mathfrak p$ of $\mathcal O_K$, return a Gram matrix `M` of the `i`th Jordan block of `g`, with coefficients in `E`. `M` is such that any hermitian lattice over $E/K$ with Gram matrix `M` satisfies that the local genus symbol of its completion at $\mathfrak p$ is equal to the `i`th Jordan block of `g`.
