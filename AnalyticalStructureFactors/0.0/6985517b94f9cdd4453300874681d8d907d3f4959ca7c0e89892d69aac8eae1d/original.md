```
rho_to_phi_mixture(ρ_vector::AbstractVector{T}, σ_vector::AbstractVector{T}) where T<:AbstractFloat
```

Converts a vector of component number densities `ρ_vector` and diameters `σ_vector` to a vector of corresponding packing fractions `ϕ_vector` for a mixture. ϕᵢ = ρᵢπσᵢ³ / 6

# Arguments

  * `ρ_vector::AbstractVector{T}`: Vector of number densities for each component.
  * `σ_vector::AbstractVector{T}`: Vector of diameters for each component.

# Returns

  * `Vector{T}`: Vector of packing fractions for each component.

# Throws

  * `DimensionMismatch`: if length of `ρ_vector` and `σ_vector` do not match.
