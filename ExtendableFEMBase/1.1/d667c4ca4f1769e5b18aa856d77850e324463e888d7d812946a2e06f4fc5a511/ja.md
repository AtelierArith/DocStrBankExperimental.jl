```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv},
    cscmat::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

SparseMatrixCSC BをFEMatrixBlock Aに追加します。
