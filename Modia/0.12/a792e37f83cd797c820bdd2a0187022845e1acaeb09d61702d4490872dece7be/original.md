```
getSignal(instantiatedModel::Modia.InstantiatedModel|result::Modia.Result, name::String)
```

Returns signal `name` of the result present in instantiatedModel (that is a [`SignalTables.Var`](@ref), [`SignalTables.Par`](@ref)) or [`SignalTables.Map`](@ref)) If `name` does not exist, an error is raised.
