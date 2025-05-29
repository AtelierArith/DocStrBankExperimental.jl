```
get_var_names(funcs::Vector{<:AbstractFlux}, dfuncs::Vector{<:AbstractStateFlux})
```

Get all variable names from flux and state flux functions. Returns (input*names, output*names, state_names).
