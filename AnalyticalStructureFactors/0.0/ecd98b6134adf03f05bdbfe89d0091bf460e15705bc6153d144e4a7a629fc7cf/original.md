```
S_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}) where {T<:AbstractFloat}
```

Returns a function `f(k)` that calculates the VW-corrected partial structure factor matrix S(k) for a multi-component hard-sphere mixture. System parameters are fixed.

# Arguments

  * `σ_vector::AbstractVector{T}`: Vector of original hard-sphere diameters.
  * `ϕ_vector::AbstractVector{T}`: Vector of original packing fractions.

# Returns

  * `Function`: A function that takes a wavevector `k` and returns the S_ij(k) matrix.
