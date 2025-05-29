```
write_vtk(name, assembly::Assembly; kwargs...)
write_vtk(name, assembly::Assembly, state::AssemblyState; kwargs...)
write_vtk(name, assembly::Assembly, history::Vector{<:AssemblyState}], dt;
    kwargs...)
```

Write the deformed geometry (and associated data) to a VTK file for visualization using ParaView.

The `state` argument may be omitted to write the original geometry to a VTK file without any associated data.

If the solution time `history` is provided, the time step must also be provided

# Keyword Arguments

  * `sections = nothing`: Cross section geometry corresponding to each point,  defined in a frame aligned with the body frame but centered around the  corresponding point. Defined as an array with shape `(3, ncross, np)` where `ncross`  is the number of points in each cross section and `np` is the number of points.
  * `scaling=1.0`: Parameter to scale the deflections (only valid if state is provided)
  * `metadata=Dict()`: Dictionary of metadata for the file(s)
