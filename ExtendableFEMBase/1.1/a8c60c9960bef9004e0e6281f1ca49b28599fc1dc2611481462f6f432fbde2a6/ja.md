```julia
addblock_matmul!(
    a::ExtendableFEMBase.FEVectorBlock{Tv},
    B::ExtendableSparse.AbstractExtendableSparseMatrixCSC{Tv, Ti<:Integer},
    b::ExtendableFEMBase.FEVectorBlock{Tv};
    factor
)

```

FEVectorBlock a に行列ベクトル積 B と b を加えます。
