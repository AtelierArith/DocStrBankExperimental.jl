```julia
SecondPiolaKirchoffStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    λ⃗::Array{R, 1},
    p;
    ad_type,
    kwargs...
) -> Any

```

Returns the second PK stress tensor for the hyperelastic model `ψ` with the principle stretches `λ⃗` with parameters `p`.

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `λ⃗::Vector`: Vector of principal stretches
  * `p`: Model parameters
  * `ad_type`: Automatic differentiation backend (see `ADTypes.jl`)
