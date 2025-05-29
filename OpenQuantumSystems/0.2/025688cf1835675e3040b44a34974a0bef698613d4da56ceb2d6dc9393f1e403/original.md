```
evolution_exact(rho0, tspan, Hamiltonian; diagonalize = false)
```

Calculate exact time evolution of the `rho0` inplace based on $U(t)$.  The `diagonalize` argument decompose Hamiltonian into $\lambda_i, S, S^{-1}$ and calculate the exponential using eigenvalue decomposition. See [`evolutionOperator`](@ref). This method returns tspan and Vector of Operators.
