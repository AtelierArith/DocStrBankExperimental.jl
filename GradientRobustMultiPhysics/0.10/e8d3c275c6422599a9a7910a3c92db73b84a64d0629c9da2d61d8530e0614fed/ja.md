```julia
add_rhsdata!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator
) -> Int64

```

指定された位置にPDEDescriptionの右辺に与えられたPDEOperatorを追加します。PDEDescriptionの対応するRHSブロック内の演算子のIDが返されます。
