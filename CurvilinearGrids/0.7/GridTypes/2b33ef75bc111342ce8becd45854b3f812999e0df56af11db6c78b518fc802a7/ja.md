```
rtheta_grid((r0, θ0), (r1, θ1), (ni_cells, nj_cells), discretization_scheme::Symbol, backend=CPU(), T=Float64) -> CurvilinearGrid2D
```

`r` と `θ` に基づいて等間隔の極座標グリッドを作成します。
