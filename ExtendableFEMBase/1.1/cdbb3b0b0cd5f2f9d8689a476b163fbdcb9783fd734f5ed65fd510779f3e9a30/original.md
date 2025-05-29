```julia
addblock_matmul!(
    a::AbstractArray{Tv, 1},
    B::ExtendableFEMBase.FEMatrixBlock{Tv, Ti},
    b::AbstractArray{Tv, 1};
    factor,
    transposed
)

```

Adds matrix-vector product B times b to FEVectorBlock a.
