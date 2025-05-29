```
Gdef = okada(G::GMTgrid; kw...)
```

### Args

  * `G`: A grid defining the region and the grid spacing where the deformation will be computed.
  * `x_start`: The x coordinate of the fault's start (UpperLeft corner of the fault plane).
  * `y_start`: The y coordinate of the fault's start.
  * `W`: The width of the fault in km.
  * `L`: The length of the fault in km.
  * `depth`: The depth of the fault top center in km (`depth` > 0).
  * `strike`: The strike of the fault trace direction (0 to 360° relative to North) defined so that  the fault dips to the right side of the trace.
  * `dip`: The dip of the fault in degrees (angle between the fault plane and the horizontal plane).
  * `rake`: Direction the hanging wall moves during rupture, measured relative to the fault STRIKE (-180 to 180°).
  * `slip`: Dislocation in `rake` direction (km when `G` is in geographic coordinates, length unit when in cartesian).
  * `open`: dislocation in tensile component (same unit as `slip`).
  * `nu`: The Poisson's ratio, default is 0.25 for an isotropic medium.
