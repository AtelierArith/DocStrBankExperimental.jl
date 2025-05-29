```
rthetaphi_grid((r0, θ0, ϕ0), (r1, θ1, ϕ1), (ni_cells, nj_cells, nk_cells), discretization_scheme::Symbol; backend=CPU(), T=Float64, is_static=true) -> CurvilinearGrid3D
```

開始/終了ポイントとセル解像度を使用して球極グリッドを生成します。
