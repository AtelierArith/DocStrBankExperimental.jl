```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv},
    B::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

ExtendableSparseMatrix BをFEMatrixBlock Aに追加します。
