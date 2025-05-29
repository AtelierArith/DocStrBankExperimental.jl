```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     k_wavevector::T, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Calculates the partial structure factor matrix S_ij(k) for a multi-component mixture using the Random Phase Approximation (RPA). The reference system is a hard-sphere mixture with Verlet-Weiss corrections. The perturbation potential for each pair (i,j) is assumed to be of Yukawa form.

The RPA formula used is: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled where βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*Yukawa_ij(k).

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters for each component (reference system).
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions for each component (reference system).
  * `k_wavevector::T`: Magnitude of the wavevector.
  * `A_matrix::AbstractMatrix{T}`: Matrix of Yukawa amplitudes Aᵢⱼ for each pair (i,j).                                Aᵢⱼ is the amplitude for the interaction between component i and j.
  * `Z_matrix::AbstractMatrix{T}`: Matrix of Yukawa inverse screening lengths zᵢⱼ for each pair (i,j).

# Returns

  * `Matrix{T}`: The n x n real-valued partial structure factor matrix S_ij(k).
