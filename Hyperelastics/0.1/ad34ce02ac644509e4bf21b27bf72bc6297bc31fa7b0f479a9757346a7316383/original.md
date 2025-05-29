```julia
CauchyStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    F::Array{S, 2},
    p;
    kwargs...
)

```

Returns the Cauchy stress tensor for the hyperelastic model `ψ` with the deformation gradient `F` with parameters `p`.

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `F::Matrix`: Deformation gradient matrix
  * `p`: Model parameters
  * `ad_type`: Automatic differentiation backend (see `ADTypes.jl`)
