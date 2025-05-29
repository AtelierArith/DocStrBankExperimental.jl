```
export_parameters(model; include_links=true)
export_parameters(parameters; include_links=true)
```

Write all parameters into a `Dict{Symbol, Any}`. For link and alias parameter, only their current value is stored, the linking information is not. Set `include_links=false` to suppress the writing of link and alias parameters.

Use [`assign_parameters!`](@ref) to restore the parameters values from the container created here.
