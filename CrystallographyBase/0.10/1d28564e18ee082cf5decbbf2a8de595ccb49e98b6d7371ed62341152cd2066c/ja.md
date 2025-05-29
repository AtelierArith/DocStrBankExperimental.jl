```
supercell(cell::Cell, repfactors::AbstractMatrix{<:Integer})
supercell(cell::Cell, repfactors::AbstractVector{<:Integer})
supercell(cell::Cell, repfactor::Integer)
```

`cell`からスーパーセルを作成します。

!!! note
    現在、整数の複製のみがサポートされています。

