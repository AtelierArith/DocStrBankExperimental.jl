```
grid_to_surface_panels(xyz, ns, nc;
    mirror = false,
    fcore = (c, Δs) -> 1e-3,
    spacing_s = Cosine(),
    spacing_c = Uniform(),
    interp_s = (x, y, xpt) -> FLOWMath.linear(x, y, xpt),
    interp_c = (x, y, xpt) -> FLOWMath.linear(x, y, xpt))
```

Discretize a potentially curved lifting surface defined by a grid with dimensions (3, i, j) where `i` corresponds to the chordwise direction (ordered from leading edge to trailing edge) and `j` corresponds to the spanwise direction (ordered from left to right) into `ns` spanwise and `nc` chordwise panels with associated vortex rings according to the spanwise discretization scheme `spacing_s` and chordwise discretization scheme `spacing_c`.  The bound vortex will be placed at the 1/4 chord and the control point will be placed at the 3/4 chord of each panel.

Return a grid with dimensions (3, i, j) containing the panel corners, a vector  of ratios to place control points when converting to surface panels, and a matrix with dimensions (i, j) containing the generated panels.

# Arguments

  * `xyz`: grid of dimensions (3, i, j) where where `i` corresponds to the  chordwise direction and `j` corresponds to the spanwise direction.
  * `ns`: number of spanwise panels
  * `nc`: number of chordwise panels

# Keyword Arguments

  * `mirror`:  mirror the geometry across the X-Z plane? defaults to `false`.
  * `fcore`: function for setting the finite core size based on the chord length      (in the x-direction) and/or the panel width (in the y/z directions).      Defaults to `(c, Δs) -> 1e-3`
  * `spacing_s`: spanwise discretization scheme, defaults to `Cosine()`
  * `spacing_c`: chordwise discretization scheme, defaults to `Uniform()`
  * `interp_s`: spanwise interpolation function, defaults to linear interpolation
  * `interp_c`: chordwise interpolation function, defaults to linear interpolation
