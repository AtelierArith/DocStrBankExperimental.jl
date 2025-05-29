```julia
replace_operator!(
    PDE::GradientRobustMultiPhysics.PDEDescription,
    position,
    id::Int64,
    O::GradientRobustMultiPhysics.AbstractPDEOperator;
    equation_name
)

```

指定された位置のPDEDescriptionの左辺にあるid番目の演算子を、与えられたPDEOperatorで置き換えます。
