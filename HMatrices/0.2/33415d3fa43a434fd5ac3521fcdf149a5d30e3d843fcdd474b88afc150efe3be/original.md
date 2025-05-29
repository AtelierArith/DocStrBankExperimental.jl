```
mutable struct HMatrix{R,T} <: AbstractMatrix{T}
```

A hierarchial matrix constructed from a `rowtree` and `coltree` of type `R` and holding elements of type `T`.
