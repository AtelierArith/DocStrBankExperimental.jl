```julia
apply_penalties!(
    A::ExtendableSparse.AbstractExtendableSparseMatrixCSC,
    fixed_dofs,
    penalty
)

```

sets penalty to the diagonal entries of fixed_dofs in A
