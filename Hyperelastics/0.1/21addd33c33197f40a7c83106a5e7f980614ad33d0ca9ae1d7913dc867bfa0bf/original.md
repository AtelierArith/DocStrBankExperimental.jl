```julia
StrainEnergyDensity(
    ψ::Hyperelastics.AbstractHyperelasticModel{T},
    _::Array{R, 1},
    p
) -> Any

```

Returns the strain energy density for the hyperelastic model `ψ` with the principle stretches `λ⃗` with parameters `p`.

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `λ⃗::Vector`: Vector of principal stretches
  * `p`: Model parameters
