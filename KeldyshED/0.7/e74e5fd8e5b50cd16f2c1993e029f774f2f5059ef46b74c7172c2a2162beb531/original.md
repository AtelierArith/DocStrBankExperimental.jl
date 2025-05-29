```julia
density_matrix(ed::KeldyshED.EDCore, β::Real) -> Vector

```

Compute the equilibrium density matrix $\hat\rho = e^{-\beta\hat H} / Z$ at an inverse temperature $\beta$ represented in the eigenbasis of the Hamiltonian $\hat H$. The density matrix is returned as a vector of diagonal blocks corresponding to invariant subspaces of $\hat H$.
