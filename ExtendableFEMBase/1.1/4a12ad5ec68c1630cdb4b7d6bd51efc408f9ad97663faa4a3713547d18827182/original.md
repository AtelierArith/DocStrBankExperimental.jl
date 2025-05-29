```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv},
    B::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

Adds ExtendableSparseMatrix B to FEMatrixBlock A.
