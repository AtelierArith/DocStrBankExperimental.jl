```
copy_axis(;
    destination::DafWriter,
    source::DafReader,
    axis::AbstractString,
    [rename::Maybe{AbstractString} = nothing,
    default::Union{Nothing, UndefInitializer} = undef]
)::Nothing
```

Copy an `axis` from some `source` [`DafReader`](@ref) into some `destination` [`DafWriter`](@ref).

The axis is fetched using the `name` and the `default`. If `rename` is specified, store the axis using this name.
