```
JuMP.set_name(vref::GeneralVariableRef, name::String)::Nothing
```

Extend `JuMP.set_name` to set the name of `vref`. It relies on `JuMP.set_name`  being defined for the underlying `DispatchVariableRef`, otherwise an  `ArgumentError` is thrown.
