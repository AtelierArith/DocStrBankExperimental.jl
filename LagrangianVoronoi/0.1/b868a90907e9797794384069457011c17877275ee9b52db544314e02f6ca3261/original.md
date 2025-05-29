```
relaxation_step!(grid::VoronoiGrid, dt::Float64; rusanov::Bool = true)
```

Update the variables by taking into account the repair velocity `dv`. The repair velocity should be known before the `relalaxation_step!` is called. See `find_dv!`. The mass, momentum and energy of each cell is updated by solving one step of an advection problem. A keyword boolean argument `rusanov` controls the use of a Rusanov approximate Riemann solver. The Rusanov flux is recommended to prevent the generation of new extrema (like negative density) and decrease of entropy. This is a second step of the mesh relaxation procedure (or maybe third, if your simulation involves a multiphase projector).
