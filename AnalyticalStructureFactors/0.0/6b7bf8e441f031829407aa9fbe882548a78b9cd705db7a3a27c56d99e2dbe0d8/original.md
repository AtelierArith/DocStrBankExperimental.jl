```
S_RPA_mixture_SALR(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                   A_attr_matrix::AbstractMatrix{T}, Z_attr_matrix::AbstractMatrix{T},
                   A_rep_matrix::AbstractMatrix{T}, Z_rep_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Returns a function `f(k)` that calculates the RPA partial structure factor matrix S_ij(k) for a multi-component SALR mixture. System and potential parameters are fixed.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `A_attr_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aᵃᵢⱼ for the attractive Yukawa component.
  * `Z_attr_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zᵃᵢⱼ for the attractive Yukawa component.
  * `A_rep_matrix::AbstractMatrix{T}`: Matrix of amplitudes Aʳᵢⱼ for the repulsive Yukawa component.
  * `Z_rep_matrix::AbstractMatrix{T}`: Matrix of inverse screening lengths zʳᵢⱼ for the repulsive Yukawa component.

# Returns

  * `Function`: A function that takes a wavevector `k` and returns the S_ij(k) matrix.
