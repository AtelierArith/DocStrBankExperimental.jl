```
unsteady_analysis(surfaces, reference, freestream, dt; kwargs...)
```

Perform a unsteady vortex lattice method analysis.  Return an object of type [`System`](@ref) containing the final system state, a matrix of surface panels (see [`SurfacePanel`](@ref) for each surface at each time step, a matrix of surface panel properties (see [`PanelProperties`](@ref)) for each surface at each time step, and a matrix of wake panels (see [`WakePanel`](@ref)) for each surface at each time step.

# Arguments

  * `surfaces`:

      * Grids of shape (3, nc+1, ns+1) which represent lifting surfaces or
      * Matrices of surface panels (see [`SurfacePanel`](@ref)) of shape

    (nc, ns)  where `nc` is the number of chordwise panels and `ns` is the number of  spanwise panels. Alternatively, a vector containing surface shapes/positions  at each time step (including at `t=0`) may be provided to model  moving/deforming lifting surfaces.
  * `reference`: Reference parameters (see [`Reference`](@ref))
  * `freestream`: Freestream parameters for each time step (see [`Freestream`](@ref))
  * `dt`: Time step vector

# Keyword Arguments

  * `symmetric`: Flags indicating whether a mirror image (across the X-Z plane) should  be used when calculating induced velocities, defaults to `false` for each surface
  * `initial_wakes`: Vector of initial wakes corresponding to each surface, represented  by matrices of wake panels (see [`WakePanel`](@ref)) of shape (nw, ns) where  `nw` is the number of chordwise wake panels and `ns` is the number of  spanwise panels. Defaults to no wake panels for each surface
  * `initial_circulation`: Vector containing the initial circulation of all surface  panels in the system.  Defaults to `zeros(N)` where `N` is the total number  of surface panels in `surfaces`.
  * `nwake`: Maximum number of wake panels in the chordwise direction for each  surface.  Defaults to `length(dx)` for all surfaces.
  * `surface_id`: Surface ID for each surface.  The finite core model is disabled  when calculating the influence of surfaces/wakes that share the same ID.
  * `wake_finite_core`: Flag for each wake indicating whether the finite core  model should be enabled when calculating the wake's influence on itself and  surfaces/wakes with the same surface ID.  Defaults to `true` for each surface.
  * `save`: Time indices at which to save the time history, defaults to `1:length(dx)`
  * `calculate_influence_matrix`: Flag indicating whether the aerodynamic influence  coefficient matrix needs to be calculated.  Re-using the same AIC matrix  will (slightly) reduce calculation times when the underlying geometry has not changed.  Defaults to `true`.  Note that this argument only affects the pre-allocated  version of this function.
  * `near_field_analysis`: Flag indicating whether a near field analysis should be  performed to obtain panel velocities, circulation, and forces for the final  time step. Defaults to `true`.
  * `derivatives`: Flag indicating whether the derivatives with respect to the  freestream variables should be calculated for the final time step. Defaults  to `true`.
