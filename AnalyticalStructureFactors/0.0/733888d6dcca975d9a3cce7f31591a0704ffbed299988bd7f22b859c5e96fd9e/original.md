```
phi_to_rho_mixture(ϕ_vector::AbstractVector{T}, σ_vector::AbstractVector{T}) where T<:AbstractFloat
```

Converts a vector of component packing fractions `ϕ_vector` and diameters `σ_vector` to a vector of corresponding number densities `ρ_vector` for a mixture. ρᵢ = 6ϕᵢ / (πσᵢ³)

# Arguments

  * `ϕ_vector::AbstractVector{T}`: Vector of packing fractions for each component.
  * `σ_vector::AbstractVector{T}`: Vector of diameters for each component.

# Returns

  * `Vector{T}`: Vector of number densities for each component.

# Throws

  * `DimensionMismatch`: if length of `ϕ_vector` and `σ_vector` do not match.
