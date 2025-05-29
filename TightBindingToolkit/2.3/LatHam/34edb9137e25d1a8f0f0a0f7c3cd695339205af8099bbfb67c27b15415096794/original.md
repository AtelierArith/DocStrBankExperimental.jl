```julia
DiagonalizeHamiltonian!(H::LatticeHamiltonian)
```

Diagonalizes the Hamiltonian stored in `H` and stores the eigenvalues and eigenvectors in `H.bands` and `H.states` respectively. Calculates the bandwidth too.
