```
getSignal(signalTable, name::String)
```

Returns signal `name` from `signalTable` (that is a [`Var`](@ref), a [`Par`](@ref) or a [`Map`](@ref)). If `name` does not exist, an error is raised.
