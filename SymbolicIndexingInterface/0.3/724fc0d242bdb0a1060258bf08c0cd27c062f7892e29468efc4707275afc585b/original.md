```
struct ParameterIndexingProxy
```

This struct wraps any struct implementing the value provider and index provider interfaces. It allows `getindex` and `setindex!` operations to get/set parameter values. Requires that the wrapped type support [`getp`](@ref) and [`setp`](@ref) for getting and setting parameter values respectively.
