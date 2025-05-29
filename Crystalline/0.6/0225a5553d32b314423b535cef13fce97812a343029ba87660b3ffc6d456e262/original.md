```
SymmetryVector(n::AbstractSymmetryVector) -> SymmetryVector
```

Return a `SymmetryVector` realization of `n`. If `n` is already a `SymmetryVector`, return `n` directly; usually, the returned value will directly reference information in `n` (i.e., will not be a copy).
