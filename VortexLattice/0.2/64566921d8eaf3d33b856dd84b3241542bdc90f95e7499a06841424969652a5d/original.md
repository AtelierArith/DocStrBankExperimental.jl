```
System{TF}
```

Contains pre-allocated storage for internal system variables.

# Fields:

  * `AIC`: Aerodynamic influence coefficient matrix from the surface panels
  * `w`: Normal velocity at the control points from external sources and wakes
  * `Γ`: Circulation strength of the surface panels
  * `V`: Velocity at the wake vertices for each surface
  * `grids`: Grids of the surfaces, represented by matrices of vertices
  * `ratios`: Ratios of the locations of each control point on each panel
  * `surfaces`: Surfaces, represented by matrices of surface panels
  * `invert_normals`: Flags indicating whether the normals of each surface should      be inverted (used for the nonlinear VLM)
  * `sections`: Section properties for each surface (Used as part of nonlinear VLM)
  * `properties`: Surface panel properties for each surface
  * `wakes`: Wake panel properties for each surface
  * `trefftz`: Trefftz panels associated with each surface
  * `reference`: Pointer to reference parameters associated with the system (see [`Reference`](@ref))
  * `freestream`: Pointer to current freestream parameters associated with the system (see [`Freestream`](@ref))
  * `symmetric`: Flags indicating whether each surface is symmetric across the X-Z plane
  * `nwake`: Number of chordwise wake panels to use from each wake in `wakes`,
  * `surface_id`: Surface ID for each surface.  The finite core model is disabled  when calculating the influence of surfaces/wakes that share the same ID.
  * `trailing_vortices`: Flags to enable/disable trailing vortices
  * `wake_finite_core`: Flag for each wake indicating whether the finite core  model should be enabled when calculating the wake's influence on itself and  surfaces/wakes with the same surface ID.
  * `near_field_analysis`: Flag indicating whether a near field analysis has been  performed for the current system state
  * `derivatives`: Flag indicating whether the derivatives with respect to the  freestream variables have been calculated
  * `dw`: Derivatives of the R.H.S. with respect to the freestream variables
  * `dΓ`: Derivatives of the circulation strength with respect to the freestream variables
  * `dproperties`: Derivatives of the panel properties with respect to the freestream variables
  * `wake_shedding_locations`: Wake shedding locations for each surface
  * `Vcp`: Velocity due to surface motion at the control points
  * `Vh`: Velocity due to surface motion at the horizontal bound vortex centers
  * `Vv`: Velocity due to surface motion at the vertical bound vortex centers
  * `Vte`: Velocity due to surface motion at the trailing edge vertices
  * `dΓdt`: Derivative of the circulation strength with respect to non-dimensional time
