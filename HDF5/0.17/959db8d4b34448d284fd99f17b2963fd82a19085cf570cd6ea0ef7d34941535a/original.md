```
h5open(file_image::Vector{UInt8}, mode::AbstractString="r";
    name=nothing,
    fapl=FileAccessProperties(),
    increment=8192,
    backing_store=false,
    write_tracking=false,
    page_size=524288,
    pv...
)
```

Open a file image contained in a `Vector{UInt8}`. See [`API.h5p_set_file_image`](@ref).

Unlike [`Drivers.Core`](@ref) the default here is not to use a backing store.
