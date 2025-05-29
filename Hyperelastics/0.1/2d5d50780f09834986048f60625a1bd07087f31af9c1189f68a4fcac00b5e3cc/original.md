```julia
CauchyStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    λ⃗::Array{R, 1},
    p;
    kwargs...
) -> Any

```

Returns the Cauchy stress tensor for the hyperelastic model `ψ` with the principle stretches `λ⃗` with parameters `p`.

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `λ⃗::Vector`: Vector of principal stretches
  * `p`: Model parameters
  * `ad_type`: Automatic differentiation backend (see `ADTypes.jl`)
