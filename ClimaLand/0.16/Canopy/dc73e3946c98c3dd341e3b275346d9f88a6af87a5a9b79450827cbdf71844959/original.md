```
initialize_auxiliary(
    model::CanopyModel{FT},
    coords,
) where {FT}
```

Creates the auxiliary state vector of the `CanopyModel` and returns  it as a ClimaCore.Fields.FieldVector.

The input `coords` is usually a ClimaCore Field object.

This function loops over the components of the `CanopyModel` and appends each component models auxiliary state vector into a single state vector, structured by component name.
