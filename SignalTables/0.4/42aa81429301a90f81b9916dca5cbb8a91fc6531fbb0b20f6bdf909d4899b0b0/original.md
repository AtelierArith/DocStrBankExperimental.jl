```
getSignalInfo(signalTable, name::String)
```

Returns signal, but [`Var`](@ref) or [`Par`](@ref)) without :values or :value but instead with :*eltypeOrType (eltype of the values if AbstractArray, otherwise typeof the values) and :*size (if defined on the values)

If `name` does not exist, an error is raised.

This function is useful if only the attributes of a signal are needed, but not their values (returning the attributes might be a *cheap* operation, whereas returning the values might be an *expensive* operation).
