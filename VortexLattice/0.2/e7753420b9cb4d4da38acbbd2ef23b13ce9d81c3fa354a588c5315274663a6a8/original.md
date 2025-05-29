```
wing_to_grid(xle, yle, zle, chord, theta, phi, ns, nc;
    fc = fill(x -> 0, length(xle)),
    mirror = false,
    fcore = (c, Δs) -> 1e-3,
    spacing_s = Cosine(),
    spacing_c = Uniform(),
    interp_s = (x, y, xpt) -> FLOWMath.linear(x, y, xpt))
```

Discretize a wing into `ns` spanwise and `nc` chordwise panels with associated vortex rings according to the spanwise discretization scheme `spacing_s` and chordwise discretization scheme `spacing_c`.

Return a grid with dimensions (3, i, j) containing the panel corners, a vector  of ratios to place control points when converting to surface panels.

# Arguments

  * `xle`: leading edge x-coordinate of each airfoil section
  * `yle`: leading edge y-coordinate of each airfoil section
  * `zle`: leading edge z-coordinate of each airfoil section
  * `chord`: chord length of each airfoil section
  * `theta`: twist of each airfoil section
  * `phi`: dihedral angle of each airfoil section, defined by a right hand rotation about the x-axis
  * `ns`: number of spanwise panels
  * `nc`: number of chordwise panels
  * `fc`: (optional) camber line function y=f(x) of each airfoil section
  * 'reference_line': 2D array, each row is the x, y coordinate of the reference point of the airfoil.      This allows xle, yle, and zle to be defined about points that are not the leading edge
  * `mirror`:  mirror the geometry across the X-Z plane?, defaults to `false`
  * `fcore`: function for setting the finite core size based on the chord length      (in the x-direction) and/or the panel width (in the y/z directions).      Defaults to `(c, Δs) -> 1e-3`
  * `spacing_s`: spanwise discretization scheme, defaults to `Cosine()`
  * `spacing_c`: chordwise discretization scheme, defaults to `Uniform()`
  * `interp_s`: interpolation function between spanwise stations, defaults to linear interpolation
  * 'invert_cambers': invert the camber of the grid, defaults to `false`.      used in generating rotors/turbines
