```
entropy_mutual(ρAB::QuantumObject, selA, selB; kwargs...)
```

Calculates the [quantum mutual information](https://en.wikipedia.org/wiki/Quantum_mutual_information) $I(A:B) = S(\hat{\rho}_A) + S(\hat{\rho}_B) - S(\hat{\rho}_{AB})$ between subsystems $A$ and $B$.

Here, $S$ is the [Von Neumann entropy](https://en.wikipedia.org/wiki/Von_Neumann_entropy), $\hat{\rho}_{AB}$ is the density matrix of the entire system, $\hat{\rho}_A = \textrm{Tr}_B \left[ \hat{\rho}_{AB} \right]$, $\hat{\rho}_B = \textrm{Tr}_A \left[ \hat{\rho}_{AB} \right]$.

# Notes

  * `ρAB` can be either a [`Ket`](@ref) or an [`Operator`](@ref).
  * `selA` specifies the indices of the sub-system `A` in `ρAB.dimensions`. See also [`ptrace`](@ref).
  * `selB` specifies the indices of the sub-system `B` in `ρAB.dimensions`. See also [`ptrace`](@ref).
  * `kwargs` are the keyword arguments for calculating Von Neumann entropy. See also [`entropy_vn`](@ref).
