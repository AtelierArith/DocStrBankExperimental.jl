```
JuMP.delete(model::InfiniteModel,
            prefs::AbstractArray{<:GeneralVariableRef})::Nothing
```

Extend `JuMP.delete` to delete a group of dependent infinite parameters and their dependencies. An `ArgumentError` is thrown if `prefs` are not dependent infinite parameters.
