```julia
addblock_matmul!(
    a::ExtendableFEMBase.FEVectorBlock{Tv},
    B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti},
    b::ExtendableFEMBase.FEVectorBlock{Tv};
    factor,
    transposed
)

```

FEVectorBlock a に行列ベクトル積 B と b (または transposed = true の場合は B' と b) を加えます。
