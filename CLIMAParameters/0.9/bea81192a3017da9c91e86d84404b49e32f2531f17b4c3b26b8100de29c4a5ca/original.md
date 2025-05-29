```
get_parameter_values(
    pd::AbstractTOMLDict,
    names::Union{String,Vector{String}},
    component::String
)

get_parameter_values(
    pd::AbstractTOMLDict,
    name_map::Union{Dict, Vector{Pair}, NTuple{N, Pair}, Vararg{Pair}},
    component::String
)
```

Given a toml dict and a list of parameter names, returns a NamedTuple of the  parameters and their values. If a component is specified, the parameter is logged as being used in that component.

Instead of a list of parameter names, this can take an iterable mapping from parameter names to variable names in code. Then, this function retrieves all parameters  from the long names and returns a NamedTuple where the keys are the variable names.
