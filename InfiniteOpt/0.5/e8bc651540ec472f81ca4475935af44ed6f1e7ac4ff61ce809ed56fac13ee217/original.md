```
parameter_list(vref::InfiniteVariableRef)::Vector{GeneralVariableRef}
```

Return a vector of the parameter references that `vref` depends on. This is primarily an internal method where [`parameter_refs`](@ref parameter_refs(vref::InfiniteVariableRef)) is intended as the preferred user function.
