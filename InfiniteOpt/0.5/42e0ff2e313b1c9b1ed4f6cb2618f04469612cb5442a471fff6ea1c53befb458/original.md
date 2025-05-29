```
parameter_list(dref::DerivativeRef)::Vector{GeneralVariableRef}
```

Return a vector of the parameter references that `dref` depends on. This is primarily an internal method where [`parameter_refs`](@ref parameter_refs(::DerivativeRef)) is intended as the preferred user function.
