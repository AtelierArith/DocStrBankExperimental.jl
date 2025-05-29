```
h5merge(
    output_file::AbstractString,
    directories::AbstractVector{<:AbstractString};
    include_base_dir::Bool=true,
    cleanup::Bool=false,
    kwargs...)
```

Add all files in multiple directories (and their subdirectories) to an HDF5 `output_file`
