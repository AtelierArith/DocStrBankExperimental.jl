```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrix{Tv, Ti<:Integer};
    factor,
    transpose
)

```

Adds ExtendableSparseMatrix B to FEMatrixBlock A.
