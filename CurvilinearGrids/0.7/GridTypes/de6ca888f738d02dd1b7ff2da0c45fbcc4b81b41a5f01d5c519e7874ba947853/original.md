```
rthetaphi_grid((r0, θ0, ϕ0), (r1, θ1, ϕ1), (ni_cells, nj_cells, nk_cells), discretization_scheme::Symbol; backend=CPU(), T=Float64, is_static=true) -> CurvilinearGrid3D
```

Generate a spherical-polar grid using start/end points and cell resolution.
