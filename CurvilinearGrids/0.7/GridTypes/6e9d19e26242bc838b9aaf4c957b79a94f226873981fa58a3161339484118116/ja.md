```
axisymmetric_rectlinear_grid((x0, y0), (x1, y1), (ni_cells, nj_cells), discretization_scheme, snap_to_axis::Bool, rotational_axis::Symbol, backend=CPU(), T=Float64, is_static=true) -> AxisymmetricGrid2D
```

開始/終了ポイントとセル解像度を使用して2D軸対称直交グリッドを生成します。
