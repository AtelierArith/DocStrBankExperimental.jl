```
delete_scalar!(
    daf::DafWriter,
    name::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

Delete a scalar property with some `name` from `daf`.

If `must_exist` (the default), this first verifies the `name` scalar property exists in `daf`.
