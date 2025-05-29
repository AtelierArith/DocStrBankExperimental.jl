```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

ExtendableSparseMatrix BをFEMatrixBlock Aに追加します。
