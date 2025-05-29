```julia
BilinearForm(
    operators_linear::Vector{DataType};
    ...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}
BilinearForm(
    operators_linear::Vector{DataType},
    action::GradientRobustMultiPhysics.AbstractAction;
    kwargs...
) -> GradientRobustMultiPhysics.PDEOperator{Float64, BilinearForm, ON_CELLS}

```

same as other constructor but with operators_current = [](no other implicit dependencies)
