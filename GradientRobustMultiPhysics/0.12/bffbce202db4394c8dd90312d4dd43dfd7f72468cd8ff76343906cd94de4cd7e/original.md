```julia
addblock_matmul!(
    a::GradientRobustMultiPhysics.FEVectorBlock{Tv},
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    b::GradientRobustMultiPhysics.FEVectorBlock{Tv};
    factor,
    transposed
)

```

Adds matrix-vector product B times b (or B' times b if transposed = true) to FEVectorBlock a.
