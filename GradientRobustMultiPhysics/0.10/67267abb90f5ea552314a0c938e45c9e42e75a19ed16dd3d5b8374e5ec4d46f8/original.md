```julia
HookStiffnessOperator1D(
    μ;
    name,
    regions,
    ∇,
    store
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

constructor for a bilinearform a(u,v) = (μ ∇u,∇v) where C is the 1D stiffness tensor for given μ.
