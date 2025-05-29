```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Returns a function `f(k)` that calculates the RPA partial structure factor matrix S_ij(k) for a multi-component Square-Well mixture. System and potential parameters are fixed.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `temperature_matrix::AbstractMatrix{T}`: Matrix of dimensionless temperatures Tᵢⱼ.
  * `lambda_range_matrix::AbstractMatrix{T}`: Matrix of Square-Well ranges λᵢⱼ.

# Returns

  * `Function`: A function that takes a wavevector `k` and returns the S_ij(k) matrix.
