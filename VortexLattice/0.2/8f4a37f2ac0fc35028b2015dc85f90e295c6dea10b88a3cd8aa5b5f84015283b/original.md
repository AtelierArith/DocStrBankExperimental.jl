```
body_forces(surfaces, properties, reference, freestream, symmetric; kwargs...)
```

Return the body force coefficients given the panel properties for `surfaces`

Note that this function assumes that a near-field analysis has already been performed to obtain the panel forces.

# Arguments:

  * `surfaces`: Collection of surfaces, where each surface is represented by a  matrix of surface panels (see [`SurfacePanel`](@ref)) of shape (nc, ns)  where `nc` is the number of chordwise panels and `ns` is the number of  spanwise panels
  * `properties`: Surface properties for each surface, where surface  properties for each surface are represented by a matrix of panel properties  (see [`PanelProperties`](@ref)) of shape (nc, ns) where `nc` is the number  of chordwise panels and `ns` is the number of spanwise panels
  * `reference`: Reference parameters (see [`Reference`](@ref))
  * `freestream`: Freestream parameters (see [`Freestream`]@ref)
  * `symmetric`: (required) Flag for each surface indicating whether a mirror image (across the X-Z plane) was used when calculating induced velocities
  * `frame`: frame in which to return `CF` and `CM`, options are [`Body()`](@ref) (default), [`Stability()`](@ref), and [`Wind()`](@ref)
