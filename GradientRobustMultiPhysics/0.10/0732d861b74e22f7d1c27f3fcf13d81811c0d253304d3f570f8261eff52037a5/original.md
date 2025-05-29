```julia
addblock!(
    A::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti};
    factor,
    transpose
)

```

Adds FEMatrixBlock B to FEMatrixBlock A.
