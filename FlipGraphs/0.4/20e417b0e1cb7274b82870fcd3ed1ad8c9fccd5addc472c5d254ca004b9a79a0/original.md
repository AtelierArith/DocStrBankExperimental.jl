```
rename_edges!(D::DeltaComplex, p::Vector{<:Integer})
```

Relabel every edge(`DualEdge`) in `D`, according to the permutation `p`.

`DualEdge` 1 => `DualEdge` $p[1]$
