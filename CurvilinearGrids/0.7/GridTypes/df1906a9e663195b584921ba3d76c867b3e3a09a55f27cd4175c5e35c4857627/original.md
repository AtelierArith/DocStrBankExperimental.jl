```
rectlinear_grid((x0, y0, z0), (x1, y1, z1), (ni_cells, nj_cells, nk_cells), discretization_scheme, backend=CPU(), T=Float64, is_static=true, make_uniform=false, tile_layout=nothing, rank::Int=-1) -> CurvilinearGrid3D
```

Generate a 3D rectlinear grid using start/end points and cell resolution.
