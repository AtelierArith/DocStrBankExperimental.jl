```
raw_parameter_refs(dref::DerivativeRef)::VectorTuple
```

Return the raw [`VectorTuple`](@ref InfiniteOpt.Collections.VectorTuple) of the  parameter references that `dref` depends on. This is primarily an internal method  where [`parameter_refs`](@ref parameter_refs(::DerivativeRef))  is intended as the preferred user function.
