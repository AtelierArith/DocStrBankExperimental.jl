```
S_RPA_mixture_SALR(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                   k_wavevector::T, 
                   A_attr_matrix::AbstractMatrix{T}, Z_attr_matrix::AbstractMatrix{T},
                   A_rep_matrix::AbstractMatrix{T}, Z_rep_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Calculates the partial structure factor matrix S*ij(k) for a multi-component mixture using the Random Phase Approximation (RPA). The reference system is a hard-sphere mixture with Verlet-Weiss corrections. The perturbation potential for each pair (i,j) is assumed to be of SALR form, modeled as u*SALR = u*Yukawa*attractive - u*Yukawa*repulsive.

The RPA formula used is: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled where βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*SALR_ij(k).

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters for each component (reference system).
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions for each component (reference system).
  * `k_wavevector::T`: Magnitude of the wavevector.
  * `A_attr_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aᵃᵢⱼ for the attractive Yukawa component.
  * `Z_attr_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zᵃᵢⱼ for the attractive Yukawa component.
  * `A_rep_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aʳᵢⱼ for the repulsive Yukawa component.
  * `Z_rep_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zʳᵢⱼ for the repulsive Yukawa component.

# Returns

  * `Matrix{T}`: The n x n real-valued partial structure factor matrix S_ij(k).
