```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti};
    factor,
    transpose
)

```

FEMatrixBlock BをFEMatrixBlock Aに追加します。
