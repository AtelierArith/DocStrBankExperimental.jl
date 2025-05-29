```
RMSEVariable(short_name, model_names::Vector{String}, units::String)
```

Construct a RMSEVariable with the `short_name` of the variable, the names of the models in `model_names`, and units which map each model name to `units`.

The categories default to "ANN", "DJF", "MAM", "JJA", "SON". The root mean square errors default to `NaN`.

This is useful if all the models share the same unit.
