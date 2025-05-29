```julia
StrainEnergyDensity(
    ψ::Hyperelastics.AbstractHyperelasticModel{T<:Hyperelastics.PrincipalValueForm},
    F::Array{R, 2},
    p
) -> Any

```

Returns a function for the strain energy density function for the hyperelastic model based on calculating the principal stretches of the deformation gradient, `F`. The eigen values are found by the following procedure:

$$
C = F^T \cdot F
a = transpose(eigvecs(C))
C^\ast = (U^\ast)^2 = a^T \cdot C \cdot a
\vec{\lambda} = diag(U)
$$

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `F::Matrix`: Deformation gradient matrix
  * `p`: Model parameters
