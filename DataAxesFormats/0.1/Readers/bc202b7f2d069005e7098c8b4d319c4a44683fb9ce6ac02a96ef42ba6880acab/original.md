```
get_scalar(
    daf::DafReader,
    name::AbstractString;
    [default::Union{StorageScalar, Nothing, UndefInitializer} = undef]
)::Maybe{StorageScalar}
```

Get the value of a scalar property with some `name` in `daf`.

If `default` is `undef` (the default), this first verifies the `name` scalar property exists in `daf`. Otherwise `default` will be returned if the property does not exist.
