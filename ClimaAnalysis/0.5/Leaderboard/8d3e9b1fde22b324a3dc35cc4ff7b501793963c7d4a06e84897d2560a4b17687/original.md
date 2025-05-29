```
RMSEVariable(short_name::String,
             model_names::Vector{String},
             category_names::Vector{String},
             RMSEs,
             units::String)
```

Construct a RMSEVariable with the `short_name` of the variable, the names of the models in `model_names`, the categories in `category_names`, the root mean squared errors in `RMSEs`, and units which map each model name to `units`.

This is useful if all the models share the same unit.
