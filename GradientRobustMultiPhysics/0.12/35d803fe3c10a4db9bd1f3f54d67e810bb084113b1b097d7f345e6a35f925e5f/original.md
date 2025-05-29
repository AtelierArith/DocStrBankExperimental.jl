```julia
LaplaceOperator(
;
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, SymmetricBilinearForm, ON_CELLS}
LaplaceOperator(
    κ;
    name,
    AT,
    ∇,
    regions,
    store
) -> Union{Nothing, GradientRobustMultiPhysics.PDEOperator{Float64, SymmetricBilinearForm, ON_CELLS}}

```

constructor for a bilinearform that describes a(u,v) = κ (∇u,∇v) where kappa is some constant (diffusion) coefficient.
