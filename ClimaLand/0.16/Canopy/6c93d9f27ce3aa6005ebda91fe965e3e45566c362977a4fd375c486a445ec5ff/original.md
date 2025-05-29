```
initialize_prognostic(
    model::CanopyModel{FT},
    coords,
) where {FT}
```

Creates the prognostic state vector of the `CanopyModel` and returns it as a ClimaCore.Fields.FieldVector.

The input `state` is usually a ClimaCore Field object.

This function loops over the components of the `CanopyModel` and appends each component models prognostic state vector into a single state vector, structured by component name.
