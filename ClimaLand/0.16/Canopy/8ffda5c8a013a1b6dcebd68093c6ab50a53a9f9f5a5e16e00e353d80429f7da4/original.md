```
initialize_auxiliary(
    component::AbstractCanopyComponent,
    state,
)
```

Creates and returns a ClimaCore.Fields.FieldVector with the auxiliary variables of the canopy component  `component`, stored using the name of the component.

The input `state` is usually a ClimaCore Field object.
