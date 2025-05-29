```julia
get_property(
    ac::BiochemicalAlgorithms.AbstractSystemComponent,
    key::Symbol,
    default
) -> Any

```

Returns the property associated with the given key in `ac`. If no such property exists, returns `default`.
