```
entropy_conditional(ρAB::QuantumObject, selB; kwargs...)
```

Calculates the [conditional quantum entropy](https://en.wikipedia.org/wiki/Conditional_quantum_entropy) with respect to sub-system $B$: $S(A|B) = S(\hat{\rho}_{AB}) - S(\hat{\rho}_{B})$.

Here, $S$ is the [Von Neumann entropy](https://en.wikipedia.org/wiki/Von_Neumann_entropy), $\hat{\rho}_{AB}$ is the density matrix of the entire system, and $\hat{\rho}_B = \textrm{Tr}_A \left[ \hat{\rho}_{AB} \right]$.

# Notes

  * `ρAB` can be either a [`Ket`](@ref) or an [`Operator`](@ref).
  * `selB` specifies the indices of the sub-system `B` in `ρAB.dimensions`. See also [`ptrace`](@ref).
  * `kwargs` are the keyword arguments for calculating Von Neumann entropy. See also [`entropy_vn`](@ref).
