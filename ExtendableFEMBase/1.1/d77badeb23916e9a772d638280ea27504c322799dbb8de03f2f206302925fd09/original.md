```julia
addblock_matmul!(
    a::ExtendableFEMBase.FEVectorBlock{Tv},
    B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti},
    b::ExtendableFEMBase.FEVectorBlock{Tv};
    factor,
    transposed
)

```

Adds matrix-vector product B times b (or B' times b if transposed = true) to FEVectorBlock a.
