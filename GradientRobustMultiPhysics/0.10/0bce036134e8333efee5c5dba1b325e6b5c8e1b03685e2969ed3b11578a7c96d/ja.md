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

他のコンストラクタと同様ですが、operators_current = [](他の暗黙の依存関係はありません)
