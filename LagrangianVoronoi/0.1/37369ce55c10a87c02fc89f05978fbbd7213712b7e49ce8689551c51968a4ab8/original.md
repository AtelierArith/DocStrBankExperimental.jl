```
VoronoiGrid{T}(boundary_rect::Rectangle, dr::Float64, kwargs...)
```

This struct contains all information about geometry, the Voronoi mesh and a cell list.  Type variable `T` specifies the Voronoi Polygon, `boundary_rect` defines the computational domain and `dr` is the default resolution  (a particle will typically occupy an area of size `dr^2`). 

Keyword arguments:

  * `xperiodic::Bool`: Is our domain periodic in the horizontal direction?
  * `yperiodic::Bool`: Is our domain periodic in the vertical direction?
  * `h` the size of cells in the cell_list
  * `r_max` the maximum possible distance between neighboring cells
