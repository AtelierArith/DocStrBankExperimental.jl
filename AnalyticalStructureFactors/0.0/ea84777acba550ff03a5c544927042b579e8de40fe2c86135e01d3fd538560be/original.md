```
IS_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

Calculates the inverse of the partial structure factor matrix, S⁻¹(k), for a multi-component hard-sphere mixture using the Percus-Yevick approximation with Verlet-Weiss corrections.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of original hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of original packing fractions.
  * `k_wavevector::T`: Magnitude of the wavevector.

# Returns

  * `Matrix{Complex{T}}`: The n x n inverse structure factor matrix S⁻¹_ij(k) with VW corrections.
