```julia
set_plotting_labels(
    data
) -> Tuple{Any, Any, Matrix{String}, Any}

```

Method which can be used to construct the arrays parsed to the plotting routines for labeling. The description for electrons and holes are predefined. If one wishes to extend by labels for, e.g. mobile ionic carriers or traps, this can be done within the main file.
