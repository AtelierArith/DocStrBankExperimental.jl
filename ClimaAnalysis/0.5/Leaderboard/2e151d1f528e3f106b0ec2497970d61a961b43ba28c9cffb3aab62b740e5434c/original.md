```
RMSEVariable(short_name, model_names::Vector{String})
```

Construct a RMSEVariable with the `short_name` of the variable and the names of the models in `model_names`.

The categories default to "ANN", "DJF", "MAM", "JJA", "SON". The root mean square errors default to `NaN`. The unit for each model is missing which is denoted by an empty string.
