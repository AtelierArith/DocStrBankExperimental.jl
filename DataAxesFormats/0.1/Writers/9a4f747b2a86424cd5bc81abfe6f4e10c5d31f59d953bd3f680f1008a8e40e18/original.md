```
set_scalar!(
    daf::DafWriter,
    name::AbstractString,
    value::StorageScalar;
    [overwrite::Bool = false]
)::Nothing
```

Set the `value` of a scalar property with some `name` in `daf`.

If not `overwrite` (the default), this first verifies the `name` scalar property does not exist.
