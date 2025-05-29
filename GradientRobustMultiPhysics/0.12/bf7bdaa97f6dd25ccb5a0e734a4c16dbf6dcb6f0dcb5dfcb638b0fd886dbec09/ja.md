```julia
add_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position,
    O::GradientRobustMultiPhysics.AbstractPDEOperator;
    equation_name
) -> Tuple{Int64, Int64}

```

指定された位置にPDEDescriptionの左辺に与えられた抽象PDEOperatorを追加します。PDEDescriptionの対応するLHSブロック内の演算子のIDが返されます。
