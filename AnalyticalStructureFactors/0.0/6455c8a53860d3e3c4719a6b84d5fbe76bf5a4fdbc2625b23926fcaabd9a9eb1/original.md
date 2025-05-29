```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

Returns a function `f(k)` that calculates the RPA partial structure factor matrix S_ij(k) for a multi-component Yukawa mixture. System and potential parameters are fixed.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions.
  * `A_matrix::AbstractMatrix{T}`: Matrix of Yukawa amplitudes Aᵢⱼ.
  * `Z_matrix::AbstractMatrix{T}`: Matrix of Yukawa inverse screening lengths zᵢⱼ.

# Returns

  * `Function`: A function that takes a wavevector `k` and returns the S_ij(k) matrix.
