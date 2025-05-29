```
evolutionApproximate!(ket_array, ket0, tspan, Hamiltonian)
```

Calculate approximate time evolution of the `ket0` inplace based on $U(t)$ that is  calculated for $t_0$ and $t_\text{step}$. See [`evolutionOperator`](@ref). Argument `ket_array` is Vector of Arrays.
