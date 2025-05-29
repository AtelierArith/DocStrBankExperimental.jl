```
render_from_file(filepath, view)
render_from_file(filepath; kwargs...)
```

Renders a template from `filepath` and `view`.

!!! note
    This function simply combines `Mustache.render` and `Mustache.load` and may be deprecated in the future.

