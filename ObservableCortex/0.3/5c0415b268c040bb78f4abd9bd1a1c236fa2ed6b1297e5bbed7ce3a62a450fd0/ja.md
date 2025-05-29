```
axes(m, b)
```

`Montage m` が与えられたとき、指定された半球 `b::BrainStructure` に対応するモンタージュ内のすべての軸をリストする `Vector{Axis3}` を取得します（`CORTEX_LEFT`、`CORTEX_RIGHT`、またはそれらの略語 `L` と `R` のいずれかである必要があります）。
