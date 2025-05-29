```
export_parameters!(container, model; include_links=true)
export_parameters!(container, parameters; include_links=true)
```

Write all parameters into the given `container`. The parameters are `push!`-ed as `name => value` pairs. For link and alias parameter, only their current value is stored, the linking information is not. Set `include_links=false` to suppress the writing of link and alias parameters.

Use [`assign_parameters!`](@ref) to restore the parameters values from the container created here.
