```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Vector{Int64},
    O::GradientRobustMultiPhysics.PDEOperator;
    equation_name
) -> Union{Nothing, Int64}

```

指定された位置にPDEDescriptionの左辺に与えられた線形PDEOperatorを追加します。オプションで、方程式の名前を変更することができます。PDEDescriptionの対応するLHSブロック内の演算子のIDが返されます。
