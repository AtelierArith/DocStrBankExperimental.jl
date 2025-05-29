```
JuMP.delete(model::InfiniteModel, fref::ParameterFunctionRef)::Nothing
```

Extend `JuMP.delete` to delete parameter functions and their dependencies. Errors  if `fref` is invalid, meaning it has already been deleted or it belongs to  another model.
