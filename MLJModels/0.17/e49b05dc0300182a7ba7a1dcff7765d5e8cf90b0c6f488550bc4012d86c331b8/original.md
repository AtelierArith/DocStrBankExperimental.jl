```
info(name::String; pkg=nothing, interactive=false)
```

Return the metadata for the registered model type having the specified `name`. The key-word argument `pkg` is required in the case of duplicate names, unless `interactive=true` is specified instead.

To instead return the model document string (without importing defining code) do `doc(name; pkg=...)`

See also [`doc`](@ref).
