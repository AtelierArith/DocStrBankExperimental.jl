```
S_RPA_mixture_SALR(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                   A_attr_matrix::AbstractMatrix{T}, Z_attr_matrix::AbstractMatrix{T},
                   A_rep_matrix::AbstractMatrix{T}, Z_rep_matrix::AbstractMatrix{T}, 
                   k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

Calculates the RPA partial structure factor matrix S_ij(k) for a vector of k values for a multi-component SALR mixture.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `A_attr_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aᵃᵢⱼ for the attractive Yukawa component.
  * `Z_attr_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zᵃᵢⱼ for the attractive Yukawa component.
  * `A_rep_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aʳᵢⱼ for the repulsive Yukawa component.
  * `Z_rep_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zʳᵢⱼ for the repulsive Yukawa component.
  * `k_values::AbstractVector{T}`: A vector of wavevector magnitudes.

# Returns

  * `Vector{Matrix{T}}`: A vector of S*ij(k) matrices, one for each k in `k*values`.
