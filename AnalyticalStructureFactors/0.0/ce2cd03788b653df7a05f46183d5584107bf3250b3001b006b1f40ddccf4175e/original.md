```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}, 
                     k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

Calculates the RPA partial structure factor matrix S_ij(k) for a vector of k values for a multi-component Yukawa mixture.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `A_matrix::AbstractMatrix{T}`: Matrix of Yukawa amplitudes Aᵢⱼ.
  * `Z_matrix::AbstractMatrix{T}`: Matrix of Yukawa inverse screening lengths zᵢⱼ.
  * `k_values::AbstractVector{T}`: A vector of wavevector magnitudes.

# Returns

  * `Vector{Matrix{T}}`: A vector of S*ij(k) matrices, one for each k in `k*values`.
