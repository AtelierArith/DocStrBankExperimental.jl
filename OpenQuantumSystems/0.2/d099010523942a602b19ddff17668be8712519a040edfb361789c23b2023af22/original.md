```
evolution_exact(rho0, tspan, Hamiltonian; diagonalize = false)
```

Calculate approximate time evolution of the `rho0` based on $U(t)$ that is  calculated for $t_0$ and $t_\text{step}$. The `diagonalize` argument decompose Hamiltonian into $\lambda_i, S, S^{-1}$ and calculate the exponential using eigenvalue decomposition. See [`evolutionOperator`](@ref). This method returns tspan and Vector of Operators.
