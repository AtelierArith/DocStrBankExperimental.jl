```
branches(path::EinExpr[, i])
```

Return the non-terminal branches of the `path`, which correspond to intermediate tensors result of contraction steps. If `i` is specified, then only return the $i$-th `EinExpr`.

See also: [`leaves`](@ref), [`Branches`](@ref).
