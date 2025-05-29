```
getindex(xi::SkewDiagram, n::Integer)
```

Return `1` if linear index `n` corresponds to (column-major) entry in `xi.lam` which is not contained in `xi.mu`. Otherwise return `0`.
