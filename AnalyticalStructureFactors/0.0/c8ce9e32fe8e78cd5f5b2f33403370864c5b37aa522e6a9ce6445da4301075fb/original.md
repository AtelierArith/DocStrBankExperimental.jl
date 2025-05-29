```
Qk_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

Calculates Baxter's Q-matrix for a multi-component hard-sphere mixture within the Percus-Yevick approximation.

The formulas for `pR` and `pS` are based on the user's provided  implementation.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters for each component.
  * `ρ_vector::AbstractVector{T}`: Vector of number densities for each component.
  * `k_wavevector::T`: Magnitude of the wavevector.

# Returns

  * `Matrix{Complex{T}}`: The n x n Baxter Q-matrix.
