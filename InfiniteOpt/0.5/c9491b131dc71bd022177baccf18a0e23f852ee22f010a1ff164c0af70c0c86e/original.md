```
raw_parameter_refs(fref::ParameterFunctionRef)::VectorTuple
```

Return the raw [`VectorTuple`](@ref InfiniteOpt.Collections.VectorTuple) of the  parameter references that `fref` depends on. This is primarily an internal method  where [`parameter_refs`](@ref parameter_refs(::ParameterFunctionRef))  is intended as the preferred user function.
