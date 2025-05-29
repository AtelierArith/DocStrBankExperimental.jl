```julia
FVConvectionDiffusionOperator(
    beta_from::Int64;
    μ
) -> GradientRobustMultiPhysics.FVConvectionDiffusionOperator{Float64}

```

finite-volume convection diffusion operator (for cell-wise P0 rho)

  * div(μ ∇ρ + β ρ)

For μ = 0, the upwind divergence div_upw(β ρ) is generated  For μ > 0, TODO
