```julia
write_error(
    file_name::String,
    data::PLaplace.PLaplaceData,
    error::Vector{Float64}
) -> Int64

```

Writes a given error along other information corresponding to the header to a given file.
