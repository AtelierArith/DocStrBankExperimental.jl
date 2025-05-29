```
PrecomputedJacobianColorvec(jac_prototype, row_colorvec, col_colorvec)
```

Use a pre-specified `colorvec` which can be directly used for sparse differentiation. Based on whether a reverse mode or forward mode or finite differences is used, the corresponding `row_colorvec` or `col_colorvec` is used. Atmost one of them can be set to `nothing`.

## Arguments

```
- `jac_prototype`: The prototype Jacobian used for computing structural nonzeros
- `row_colorvec`: The row colorvec of the Jacobian
- `col_colorvec`: The column colorvec of the Jacobian
```

See Also: [SymbolicsSparsityDetection](@ref), [JacPrototypeSparsityDetection](@ref)
