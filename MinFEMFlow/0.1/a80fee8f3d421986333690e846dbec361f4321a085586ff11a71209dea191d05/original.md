```julia
write_to_vtk(
    fs::MinFEMFlow.FlowSolver,
    file_name::String
) -> Vector{String}

```

Writes velocity and pressure of the solved flow to a .vtu-file under the given file_name.
