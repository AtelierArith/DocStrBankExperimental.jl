```
PrecomputedJacobianColorvec(; jac_prototype, partition_by_rows::Bool = false,
    colorvec = missing, row_colorvec = missing, col_colorvec = missing)
```

Use a pre-specified `colorvec` which can be directly used for sparse differentiation. Based on whether a reverse mode or forward mode or finite differences is used, the corresponding `row_colorvec` or `col_colorvec` is used. Atmost one of them can be set to `nothing`.

## Keyword Arguments

```
- `jac_prototype`: The prototype Jacobian used for computing structural nonzeros
- `partition_by_rows`: Whether to partition the Jacobian by rows or columns (row
  partitioning is used for reverse mode AD)
- `colorvec`: The colorvec of the Jacobian. If `partition_by_rows` is `true` then this
  is the row colorvec, otherwise it is the column colorvec
- `row_colorvec`: The row colorvec of the Jacobian
- `col_colorvec`: The column colorvec of the Jacobian
```

See Also: [SymbolicsSparsityDetection](@ref), [JacPrototypeSparsityDetection](@ref)
