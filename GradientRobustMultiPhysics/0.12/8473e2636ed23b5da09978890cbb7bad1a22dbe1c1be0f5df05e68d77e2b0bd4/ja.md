```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    equation::Int64,
    O::GradientRobustMultiPhysics.PDEOperator{T, APT<:NonlinearForm};
    equation_name
)

```

指定されたPDEDescriptionの方程式に与えられた非線形PDEOperatorを追加します。オプションで、方程式の名前を変更することができます。
