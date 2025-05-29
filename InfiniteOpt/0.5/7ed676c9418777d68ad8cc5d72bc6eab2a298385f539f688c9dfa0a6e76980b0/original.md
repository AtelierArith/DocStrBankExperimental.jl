```
JuMP.delete(model::InfiniteModel, vref::GeneralVariableRef)::Nothing
```

Extend `JuMP.delete` to delete `vref` and its dependencies. It relies on  `JuMP.delete` being defined for the underlying `DispatchVariableRef`, otherwise  an `ArgumentError` is thrown.
