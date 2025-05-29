```
allocate_variables!(domain, modeldata, arrays_idx; [hostdep=false] [, kwargs...])
```

Allocate memory for Domain Variables. 

If `hostdep=false`, only internal Variables are allocated, allowing host-dependent Variables (usually state Variables and derivatives + any external dependencies) to be set to views on host-managed arrays.

See [`allocate_variables!(vars, modeldata::AbstractModelData, arrays_idx::Int)`](@ref).
