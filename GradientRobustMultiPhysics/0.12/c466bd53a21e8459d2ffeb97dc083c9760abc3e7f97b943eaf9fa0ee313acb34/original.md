```julia
ConvectionOperator(
    β::GradientRobustMultiPhysics.AbstractUserDataType,
    ncomponents::Int64;
    name,
    store,
    AT,
    ansatz_operator,
    test_operator,
    transposed_assembly,
    regions
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

constructor for a bilinearform that describes a(u,v) = ((β ⋅ ∇) u,v) with some user-specified DataFunction β. The user also has to specify the number of components (ncomponents) the convection is applied to. The operators for u and v can be changed (if this leads to something reasonable).
