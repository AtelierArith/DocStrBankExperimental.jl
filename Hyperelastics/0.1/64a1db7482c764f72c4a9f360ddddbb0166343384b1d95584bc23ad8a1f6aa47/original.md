```julia
SecondPiolaKirchoffStressTensor(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    F::Array{R, 2},
    p;
    kwargs...
) -> Any

```

Returns the second PK stress tensor for the hyperelastic model `ψ` with the deformation gradient `F` with parameters `p`.

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `F::Matrix`: Deformation gradient matrix
  * `p`: Model parameters
  * `ad_type`: Automatic differentiation backend (see `ADTypes.jl`)
