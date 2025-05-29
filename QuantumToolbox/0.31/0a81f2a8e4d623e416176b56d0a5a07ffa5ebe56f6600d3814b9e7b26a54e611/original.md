```
partial_transpose(ρ::QuantumObject, mask::Vector{Bool})
```

Return the partial transpose of a density matrix $\rho$, where `mask` is an array/vector with length that equals the length of `ρ.dims`. The elements in `mask` are boolean (`true` or `false`) which indicates whether or not the corresponding subsystem should be transposed.

# Arguments

  * `ρ::QuantumObject`: The density matrix (`ρ.type` must be [`Operator`](@ref)).
  * `mask::Vector{Bool}`: A boolean vector selects which subsystems should be transposed.

# Returns

  * `ρ_pt::QuantumObject`: The density matrix with the selected subsystems transposed.
