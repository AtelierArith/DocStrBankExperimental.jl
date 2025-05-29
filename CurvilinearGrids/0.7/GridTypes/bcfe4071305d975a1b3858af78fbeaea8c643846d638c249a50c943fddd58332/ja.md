```
rectlinear_cylindrical_grid((r0, r1), ncells, discretization_scheme, snap_to_axis=true, backend=CPU(), T=Float64, is_static=true, make_uniform=false, tile_layout=nothing, rank::Int=-1) -> CylindricalGrid1D
```

開始/終了ポイントとセル解像度を使用して1D円筒直交グリッドを生成します。
