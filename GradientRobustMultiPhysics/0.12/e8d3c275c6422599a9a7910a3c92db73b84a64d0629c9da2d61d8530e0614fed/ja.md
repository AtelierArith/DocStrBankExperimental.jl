```julia
add_rhsdata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator
) -> Int64

```

指定された位置にPDEDescriptionの右辺に指定されたPDEOperatorを追加します。PDEDescriptionの対応するRHSブロック内の演算子のIDが返されます。
