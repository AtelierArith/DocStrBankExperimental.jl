```
quantum_potts([elt::Type{<:Number}], [symmetry::Type{<:Sector}],
              [lattice::AbstractLattice]; q=3, J=1.0, g=1.0)
```

MPO for the hamiltonian of the quantum Potts model, as defined by

$$
H = - J \sum_{\langle i,j \rangle} Z_i^\dagger Z_j + Z_i Z_j^\dagger
- g \sum_i (X_i + X_i^\dagger)
$$

where the operators $Z$ and $X$ are the $q$-rotation operators satisfying $Z^q = X^q = 1$ and $ZX = \omega XZ$ where $\omega = e^{2πi/q}$.
