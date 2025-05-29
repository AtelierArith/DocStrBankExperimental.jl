```
add_axis!(
    daf::DafWriter,
    axis::AbstractString,
    entries::AbstractVector{<:AbstractString}
)::Nothing
```

Add a new `axis` to `daf`.

This first verifies the `axis` does not exist and that the `entries` are unique.
