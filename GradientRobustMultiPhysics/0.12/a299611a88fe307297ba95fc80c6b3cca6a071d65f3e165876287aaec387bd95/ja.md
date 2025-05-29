```julia
addblock_matmul!(
    a::GradientRobustMultiPhysics.FEVectorBlock{Tv},
    B::ExtendableSparse.ExtendableSparseMatrixCSC{Tv, Ti<:Integer},
    b::GradientRobustMultiPhysics.FEVectorBlock{Tv};
    factor
)

```

FEVectorBlock a に行列ベクトル積 B と b を加えます。
