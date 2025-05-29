```julia
addblock_matmul!(
    a::AbstractArray{Tv, 1},
    B::GradientRobustMultiPhysics.FEMatrixBlock{Tv, Ti},
    b::AbstractArray{Tv, 1};
    factor,
    transposed
)

```

FEVectorBlock a に行列ベクトル積 B と b を加えます。
