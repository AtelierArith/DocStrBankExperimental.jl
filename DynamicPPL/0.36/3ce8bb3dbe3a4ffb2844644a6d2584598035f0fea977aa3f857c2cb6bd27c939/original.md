```
@model(expr[, warn = false])
```

Macro to specify a probabilistic model.

If `warn` is `true`, a warning is displayed if internal variable names are used in the model definition.

# Examples

Model definition:

```julia
@model function model(x, y = 42)
    ...
end
```

To generate a `Model`, call `model(xvalue)` or `model(xvalue, yvalue)`.
