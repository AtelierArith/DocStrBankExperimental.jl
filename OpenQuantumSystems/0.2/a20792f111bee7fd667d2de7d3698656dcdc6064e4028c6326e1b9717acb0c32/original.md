```
evolutionOperatorIterator(Hamiltonian, tspan; diagonalize = true, approximate = false)
```

Resumable function that returns evolution operator as Operator type at the time t from tspan. See [`evolutionOperator`](@ref). The `diagonalize` argument decompose Hamiltonian into $\lambda_i, S, S^{-1}$ and calculate the exponential using eigenvalue decomposition. The `approximate` option asusmes that tspan is made of  equidistant points, therefore $U(t)$ has to be calculated for $t_0$ and $t_\text{step}$.
