```julia
addblock!(
    A::ExtendableFEMBase.FEMatrixBlock{Tv},
    cscmat::SparseArrays.SparseMatrixCSC{Tv, Ti<:Integer};
    factor,
    transpose
)

```

Adds SparseMatrixCSC B to FEMatrixBlock A.
