```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv, Ti},
    B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti};
    factor,
    transpose
)

```

Adds FEMatrixBlock B to FEMatrixBlock A.
