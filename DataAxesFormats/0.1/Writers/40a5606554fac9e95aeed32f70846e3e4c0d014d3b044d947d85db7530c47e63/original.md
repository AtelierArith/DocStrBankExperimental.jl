```
delete_vector!(
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

Delete a vector property with some `name` for some `axis` from `daf`.

This first verifies the `axis` exists in `daf` and that the property name isn't `name`. If `must_exist` (the default), this also verifies the `name` vector exists for the `axis`.
