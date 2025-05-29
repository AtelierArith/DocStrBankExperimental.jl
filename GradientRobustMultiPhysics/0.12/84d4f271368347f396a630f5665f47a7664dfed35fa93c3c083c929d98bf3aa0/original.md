```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

Adds ExtendableSparseMatrix B to FEMatrixBlock A.
