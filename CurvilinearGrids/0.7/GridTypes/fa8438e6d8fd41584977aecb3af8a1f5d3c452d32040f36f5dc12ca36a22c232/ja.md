```
axisymmetric_rtheta_grid(r, θ, discretization_scheme, snap_to_axis, rotational_axis::Symbol, backend=CPU()) -> AxisymmetricGrid2D
```

`r` と `θ` 座標のベクトルに基づいて極座標グリッドを作成します。回転軸は `rotational_axis` によって `:x` または `:y` として設定されます。
