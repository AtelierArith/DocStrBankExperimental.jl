```julia
write_result_to_txt(
    filename::String,
    data::PLaplace.PLaplaceData
)

```

Writes result vector to a VTK file with the given name. The file itself will be created, but the path has to exist prior. 
