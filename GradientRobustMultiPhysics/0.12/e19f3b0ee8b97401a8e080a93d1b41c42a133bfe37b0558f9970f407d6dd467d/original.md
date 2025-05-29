```julia
LagrangeMultiplier(
    operator::Type{<:??};
    name,
    AT,
    action,
    regions,
    store,
    factor
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

constructor for a bilinearform that describes a(u,v) = (A(operator(u)), id(v)) and assembles a second transposed block at the block of the transposed PDE coordinates. It is intended to use to render one unknown of the PDE the Lagrange multiplier for another unknown by putting this operator on the coressponding subdiagonal block of the PDE description.

Example: LagrangeMultiplier(Divergence) is used to render the pressure the LagrangeMultiplier for the velocity divergence constraint in the Stokes prototype.
