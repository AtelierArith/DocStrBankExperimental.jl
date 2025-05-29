```
mutable struct HMatrix{R,T} <: AbstractMatrix{T}
```

`rowtree` と `coltree` のタイプ `R` から構築され、タイプ `T` の要素を保持する階層行列。
