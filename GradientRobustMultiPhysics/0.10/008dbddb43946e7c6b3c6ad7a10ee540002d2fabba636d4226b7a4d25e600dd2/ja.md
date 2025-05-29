```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrix{Tv, Ti<:Integer};
    factor,
    transpose
)

```

ExtendableSparseMatrix BをFEMatrixBlock Aに追加します。
