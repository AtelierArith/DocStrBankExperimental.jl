```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv, Ti},
    B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti};
    factor,
    transpose
)

```

FEMatrixBlock BをFEMatrixBlock Aに追加します。
