```
entropy_linear(ρ::QuantumObject)
```

Calculates the quantum linear entropy $S_L = 1 - \textrm{Tr} \left[ \hat{\rho}^2 \right]$, where $\hat{\rho}$ is the density matrix of the system.

Note that `ρ` can be either a [`Ket`](@ref) or an [`Operator`](@ref).
