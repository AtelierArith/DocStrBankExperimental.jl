```
parameter_list(vref::SemiInfiniteVariableRef)::Vector{GeneralVariableRef}
```

Return a vector of the parameter references that `vref` depends on. This is primarily an internal method where [`parameter_refs`](@ref parameter_refs(vref::SemiInfiniteVariableRef)) is intended as the preferred user function.
