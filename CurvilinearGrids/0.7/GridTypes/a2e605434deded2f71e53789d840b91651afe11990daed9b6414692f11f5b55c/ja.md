```
rectlinear_grid(x, y, discretization_scheme::Symbol; backend=CPU(), is_static=true, make_uniform=false, tile_layout=nothing, rank::Int=-1) -> CurvilinearGrid2D
```

1Dのxおよびy座標ベクトルを使用して2Dの直交格子を生成します。
