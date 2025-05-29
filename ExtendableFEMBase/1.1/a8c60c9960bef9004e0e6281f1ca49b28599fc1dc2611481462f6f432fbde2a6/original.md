```julia
addblock_matmul!(
    a::ExtendableFEMBase.FEVectorBlock{Tv},
    B::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti<:Integer},
    b::ExtendableFEMBase.FEVectorBlock{Tv};
    factor
)

```

Adds matrix-vector product B times b to FEVectorBlock a.
