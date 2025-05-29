```
has_vector(daf::DafReader, axis::AbstractString, name::AbstractString)::Bool
```

Check whether a vector property with some `name` exists for the `axis` in `daf`. This is always true for the special `name` property.

This first verifies the `axis` exists in `daf`.
