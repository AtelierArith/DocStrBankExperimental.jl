```
rtheta_grid((r0, θ0), (r1, θ1), (ni_cells, nj_cells), discretization_scheme, snap_to_axis, rotational_axis, backend=CPU(), T=Float64) -> AxisymmetricGrid2D
```

`r` と `θ` に基づいて等間隔の軸対称極座標グリッドを作成します。回転軸は `rotational_axis` によって `:x` または `:y` に設定されます。
