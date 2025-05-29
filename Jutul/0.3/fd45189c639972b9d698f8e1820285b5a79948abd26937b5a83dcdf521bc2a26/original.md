```
MultiModel(models)
MultiModel(models, :SomeLabel)
```

A model variant that is made up of many named submodels, each a fully realized [`SimulationModel`](@ref).

`models` should be a `NamedTuple` or `Dict{Symbol, JutulModel}`.
