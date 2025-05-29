```
JuMP.name(vref::GeneralVariableRef)::String
```

Extend `JuMP.name` to return the name of `vref`. It relies on `JuMP.name` being  defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError`  is thrown.
