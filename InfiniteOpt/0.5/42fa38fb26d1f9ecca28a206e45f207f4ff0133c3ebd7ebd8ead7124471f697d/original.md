```
parameter_list(fref::ParameterFunctionRef)::Vector{GeneralVariableRef}
```

Return a vector of the parameter references that `fref` depends on. This is primarily an internal method where [`parameter_refs`](@ref parameter_refs(::ParameterFunctionRef)) is intended as the preferred user function.
