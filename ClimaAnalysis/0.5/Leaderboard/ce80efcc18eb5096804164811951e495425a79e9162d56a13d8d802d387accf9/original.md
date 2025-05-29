```
RMSEVariable(short_name, model_names::Vector{String}, units::Dict)
```

Construct a RMSEVariable with the `short_name` of the variable, the names of the models in `model_names`, and provided units in the dictionary `units` that map model name to unit.

The categories default to "ANN", "DJF", "MAM", "JJA", "SON". The root mean square errors default to `NaN`. Any missing model in the dictionary `units` will has missing unit which is denoted by an empty string.
