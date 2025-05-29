```
S_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

Calculates the partial structure factor matrix S(k) for a multi-component hard-sphere mixture using the Percus-Yevick approximation with Verlet-Weiss (VW) corrections.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of original hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of original packing fractions.
  * `k_wavevector::T`: Magnitude of the wavevector.

# Returns

  * `Matrix{T}`: The n x n real-valued partial structure factor matrix S_ij(k) with VW corrections.
