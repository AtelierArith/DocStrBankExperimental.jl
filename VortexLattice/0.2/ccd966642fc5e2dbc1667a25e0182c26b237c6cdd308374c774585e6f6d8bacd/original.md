```
grid_to_surface_panels(xyz;
    ratios = zeros(2, size(xyz, 2)-1, size(xyz, 3)-1) .+ [0.5;0.75],
    mirror = false,
    fcore = (c, Δs) -> 1e-3)
```

Construct a set of panels with associated vortex rings given a potentially curved lifting surface defined by a grid with dimensions (3, i, j) where `i` corresponds to the chordwise direction (ordered from leading edge to trailing edge) and `j` corresponds to the spanwise direction (ordered from left to right).  The leading edge of each ring vortex will be placed at the 1/4 chord and the control point will be placed at the 3/4 chord of each panel.

Return a grid with dimensions (3, i, j) containing the panel corners, a vector  of ratios to place control points when converting to surface panels, and a matrix with dimensions (i, j) containing the generated panels.

# Keyword Arguments

  * `mirror`:  mirror the geometry across the X-Z plane? defaults to `false`.
  * `fcore`: function for setting the finite core size based on the chord length      (in the x-direction) and/or the panel width (in the y/z directions).      Defaults to `(c, Δs) -> 1e-3`
