```
rectlinear_grid((x0, y0), (x1, y1), (ni_cells, nj_cells), discretization_scheme, backend=CPU(), T=Float64, is_static=true, make_uniform=false, tile_layout=nothing, rank::Int=-1) -> CurvilinearGrid2D
```

開始点/終了点とセル解像度を使用して2D直交グリッドを生成します。
