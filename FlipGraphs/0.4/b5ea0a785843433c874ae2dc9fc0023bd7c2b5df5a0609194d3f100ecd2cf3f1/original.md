```
rename_vertices!(D::DeltaComplex, p::Vector{<:Integer})
```

Relabel every vertex(`TriFace`) in `D`, according to the permutation `p`.

`TriFace` 1 => `TriFace` $p[1]$ 
