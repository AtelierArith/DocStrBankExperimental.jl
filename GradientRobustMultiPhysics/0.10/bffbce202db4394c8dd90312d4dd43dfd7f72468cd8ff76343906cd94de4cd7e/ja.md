```julia
addblock_matmul!(
    a::GradientRobustMultiPhysics.FEVectorBlock{Tv},
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    b::GradientRobustMultiPhysics.FEVectorBlock{Tv};
    factor,
    transposed
)

```

FEVectorBlock a に行列ベクトル積 B と b（または transposed = true の場合は B' と b）を加えます。
