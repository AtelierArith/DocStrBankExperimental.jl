```
current_parameter(ds::DynamicalSystem, index [,p])
```

Return the specific parameter of `ds` corresponding to `index`, which can be anything given to [`set_parameter!`](@ref). `p` defaults to [`current_parameters`](@ref) and is the parameter container to extract the parameter from, which must match layout with its default value.

Use [`parameter_name`](@ref) for an accompanying name.
