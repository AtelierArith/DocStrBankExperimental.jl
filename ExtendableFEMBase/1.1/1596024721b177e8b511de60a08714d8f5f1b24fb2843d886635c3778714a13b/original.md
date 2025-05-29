```julia
add!(
    A::ExtendableFEMBase.FEMatrix{Tv, Ti},
    B::ExtendableFEMBase.FEMatrix{Tv, Ti};
    kwargs...
)

```

Adds FEMatrix/ExtendableSparseMatrix/CSCMatrix B to FEMatrix A.
