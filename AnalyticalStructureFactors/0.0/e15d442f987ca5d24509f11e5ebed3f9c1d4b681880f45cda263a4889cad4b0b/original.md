```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         k_wavevector::T, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Calculates the partial structure factor matrix S_ij(k) for a multi-component mixture using the Random Phase Approximation (RPA). The reference system is a hard-sphere mixture with Verlet-Weiss corrections. The perturbation potential for each pair (i,j) is assumed to be of Square-Well form.

The RPA formula used is: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled where βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*SquareWell_ij(k).

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters for each component (reference system).
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions for each component (reference system).
  * `k_wavevector::T`: Magnitude of the wavevector.
  * `temperature_matrix::AbstractMatrix{T}`: Matrix of dimensionless temperatures Tᵢⱼ for each pair (i,j).                                         Tᵢⱼ is typically related to the well depth εᵢⱼ (e.g., k*B * T*abs / εᵢⱼ).
  * `lambda_range_matrix::AbstractMatrix{T}`: Matrix of Square-Well ranges λᵢⱼ for each pair (i,j)                                           (in units of the hard-sphere diameter σ of a reference component, or σᵢⱼ).

# Returns

  * `Matrix{T}`: The n x n real-valued partial structure factor matrix S_ij(k).
