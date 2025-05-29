```
viscous_step!(grid::VoronoiGrid, dt::Float64; artificial_viscosity::Bool = true)
```

Applies one forward viscous step of size `dt` to all Voronoi polygons. It assumes that the velocity deformation tensor is already computed using the `find_D!` function. It is also assumed that every polygon `p` has its dynamic viscosity `p.mu` assigned by the initial condition or otherwise. A keyword parameter controls whether Stone-Norman viscosity tensor is used to damp oscillations near shocks (yes by default).
