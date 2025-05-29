```
h5merge(
    output_file::AbstractString,
    directory::AbstractString;
    mode::AbstractString="a",
    skip_existing_entries::Bool=false,
    follow_symlinks::Bool=false,
    verbose::Bool=false,
    include_base_dir::Bool=false,
    pattern::Union{Regex,Nothing}=nothing,
    kwargs...
    )
```

Add all files in a directory (and subdirectories) to an HDF5 `output_file`
