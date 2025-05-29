```
write_vtk(name, surface_history, property_history, wake_history; kwargs...)
```

Writes unsteady simulation geometry to Paraview files for visualization.

# Arguments

  * `name`: Base name for the generated files
  * `surface_history`: Vector of surfaces at each time step, where each surface is  represented by a matrix of surface panels (see [`SurfacePanel`](@ref)) of shape  (nc, ns) where `nc` is the number of chordwise panels and `ns` is the number  of spanwise panels
  * `property_history`: Vector of surface properties for each surface at each  time step, where surface properties are represented by a matrix of panel  properties (see [`PanelProperties`](@ref)) of shape (nc, ns) where `nc` is  the number of chordwise panels and `ns` is the number of spanwise panels
  * `wake_history`: Vector of wakes corresponding to each surface at each time step,  where each wake is represented by a matrix of wake panels (see [`WakePanel`](@ref))  of shape (nw, ns) where `nw` is the number of chordwise wake panels and  `ns` is the number of spanwise panels.
  * `dt`: Time step vector

# Keyword Arguments:

  * `symmetric`: (required if `properties` is provided) Flags indicating whether a  mirror image (across the X-Z plane) was used when calculating induced velocities  for each surface.
  * `wake_length`: Distance to extend trailing vortices. Defaults to 10
  * `metadata`: Dictionary of metadata to include in generated files
