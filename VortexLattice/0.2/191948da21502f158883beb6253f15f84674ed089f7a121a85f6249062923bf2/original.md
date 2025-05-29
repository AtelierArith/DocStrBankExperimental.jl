```
write_vtk(name, surfaces, [surface_properties]; kwargs...)
write_vtk(name, wakes; kwargs...)
write_vtk(name, surfaces, wakes, [surface_properties]; kwargs...)
```

Write geometry from surfaces and/or wakes to Paraview files for visualization.

# Arguments

  * `name`: Base name for the generated files
  * `surfaces`:

      * Vector of grids of shape (3, nc+1, ns+1) which represent lifting surfaces

    or

      * Vector of matrices of shape (nc, ns) containing surface panels (see

    [`SurfacePanel`](@ref)) where `nc` is the number of chordwise panels and `ns` is the number of spanwise panels
  * `wakes`: (optional) Vector of wakes corresponding to each surface, represented  by matrices of wake panels (see [`WakePanel`](@ref)) of shape (nw, ns) where  `nw` is the number of chordwise wake panels and `ns` is the number of  spanwise panels.
  * `surface_properties`: (optional) Vector of surface panel properties for each  surface, stored as matrices of panel properties (see [`PanelProperties`](@ref))  of shape (nc, ns) where `nc` is the number of chordwise panels and `ns` is  the number of spanwise panels

# Keyword Arguments:

  * `symmetric`: (required if `surface_properties` is provided) Flags indicating whether a  mirror image (across the X-Z plane) was used when calculating induced velocities  for each surface.
  * `trailing_vortices`: Flag indicating whether the model uses trailing vortices.  Defaults to `true` when wake panels are absent, `false` otherwise
  * `xhat`: Direction in which trailing vortices extend if used. Defaults to [1, 0, 0].
  * `wake_length`: Distance to extend trailing vortices. Defaults to 10
  * `metadata`: Dictionary of metadata to include in generated files
