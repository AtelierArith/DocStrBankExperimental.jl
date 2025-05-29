```julia
apply_penalties!(
    A::ExtendableSparse.AbstractExtendableSparseMatrixCSC,
    fixed_dofs,
    penalty
)

```

は、Aのfixed_dofsの対角エントリにペナルティを設定します。
