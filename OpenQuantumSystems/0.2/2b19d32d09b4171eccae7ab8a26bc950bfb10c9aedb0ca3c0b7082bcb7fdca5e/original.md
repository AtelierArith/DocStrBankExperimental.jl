```
evolutionExact(ket0, tspan, Hamiltonian; diagonalize = true, approximate = false)
```

Calculate exact time evolution of the `ket0` state see [`evolutionOperatorIterator`](@ref).  The `diagonalize` argument decompose Hamiltonian into $\lambda_i, S, S^{-1}$ and calculate the exponential using eigenvalue decomposition. The `approximate` option asusmes that tspan is made of  equidistant points, therefore $U(t)$ has to be calculated for $t_0$ and $t_\text{step}$.
