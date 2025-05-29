```
evolutionApproximate!(op_array, op0, tspan, Hamiltonian)
```

Calculate approximate time evolution of the `op0` inplace based on $U(t)$ that is  calculated for $t_0$ and $t_\text{step}$. See [`evolutionOperator`](@ref). This method returns Vector of Arrays.
