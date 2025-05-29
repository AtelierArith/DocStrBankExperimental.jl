```julia
addblock_matmul!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv},
    cscmatB::SparseArrays.SparseMatrixCSC{Tv, Ti},
    cscmatC::SparseArrays.SparseMatrixCSC{Tv, Ti};
    factor,
    transposed
)

```

Adds matrix-matrix product B times C to FEMatrixBlock A.
