```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}, 
                         k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

Calculates the RPA partial structure factor matrix S_ij(k) for a vector of k values for a multi-component Square-Well mixture.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `temperature_matrix::AbstractMatrix{T}`: Matrix of dimensionless temperatures Tᵢⱼ.
  * `lambda_range_matrix::AbstractMatrix{T}`: Matrix of Square-Well ranges λᵢⱼ.
  * `k_values::AbstractVector{T}`: A vector of wavevector magnitudes.

# Returns

  * `Vector{Matrix{T}}`: A vector of S*ij(k) matrices, one for each k in `k*values`.
