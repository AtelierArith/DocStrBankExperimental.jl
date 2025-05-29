```
Interpolation(x, y, gridargs...; method::Symbol = :linear, kwargs...)
```

`x` 値と `y` 値のセットから補間スキームを作成します（補間される）。 `method` は補間の種類を設定し、`extrapolation_bc` は外挿境界条件を設定します（有効な `BoundaryCondition` または `NaN` のいずれか）。
