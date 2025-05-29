```
doc(name::String; pkg=nothing, interactive=false)
```

Return the documentation string for the registered model type having the specified `name`. The key-word argument `pkg` is required in the case of duplicate names, unless `interactive=true` is specified instead.
