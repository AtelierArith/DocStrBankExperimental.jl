```julia
write_result_to_vtk(
    filename::String,
    data::PLaplace.PLaplaceData
) -> Union{Nothing, Vector{String}}

```

Writes result vector to a VTK file with the given name. The file itself will be created, but the path has to exist prior. 
