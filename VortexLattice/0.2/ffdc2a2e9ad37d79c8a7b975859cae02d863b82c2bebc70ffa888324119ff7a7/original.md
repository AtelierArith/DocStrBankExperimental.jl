```
steady_analysis(surfaces, reference, freestream; kwargs...)
```

Perform a steady vortex lattice method analysis.  Return an object of type [`System`](@ref) containing the system state.

# Arguments

  * `surfaces`:

      * Vector of grids of shape (3, nc+1, ns+1) which represent lifting surfaces

    or

      * Vector of matrices of shape (nc, ns) containing surface panels (see

    [`SurfacePanel`](@ref)) where `nc` is the number of chordwise panels and `ns` is the number of spanwise panels
  * `reference`: Reference parameters (see [`Reference`](@ref))
  * `freestream`: Freestream parameters (see [`Freestream`](@ref))

# Keyword Arguments

  * `symmetric`: Flag for each surface indicating whether a mirror image across  the X-Z plane should be used when calculating induced velocities. Defaults to  `false` for each surface
  * `wakes`: Matrix of wake panels (see [`WakePanel`](@ref)) for each surface.  Each  matrix has shape (nw, ns) where `nw` is the number of chordwise wake panels  and `ns` is the number of spanwise panels for each surface, defaults to no  wake panels for each surface
  * `nwake`: Number of chordwise wake panels to use from each wake in `wakes`,  defaults to all wake panels for each surface
  * `surface_id`: Surface ID for each surface.  The finite core model is disabled  when calculating the influence of surfaces/wakes that share the same ID.  By default, all surfaces are assigned their own IDs
  * `wake_finite_core`: Flag for each wake indicating whether the finite core  model should be enabled when calculating a wake's influence on itself and  surfaces/wakes with the same surface ID.  Defaults to `true` for each surface.
  * `trailing_vortices`: Flags to enable/disable trailing vortices for each surface,  defaults to `true` for each surface
  * `xhat`: Direction in which to shed trailing vortices, defaults to `[1, 0, 0]`
  * `additional_velocity`: Function which defines additional velocity as a  function of location.
  * `fcore`: function which sets the finite core size for each surface based on  the chord length and/or the panel width. Defaults to `(c, Δs) -> 1e-3`.  Only used for grid inputs.
  * `calculate_influence_matrix`: Flag indicating whether the aerodynamic influence  coefficient matrix has already been calculated.  Re-using the same AIC matrix  will reduce calculation times when the underlying geometry has not changed.  Defaults to `true`.  Note that this argument is only valid for the pre-allocated  version of this function.
  * `near_field_analysis`: Flag indicating whether a near field analysis should be  performed to obtain panel velocities, circulation, and forces. Defaults to `true`.
  * `derivatives`: Flag indicating whether the derivatives with respect  to the freestream variables should be calculated. Defaults to `true`.
