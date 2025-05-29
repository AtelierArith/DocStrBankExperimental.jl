```
JuMP.set_binary(vref::GeneralVariableRef)
```

Define `JuMP.set_binary` for general variable references. It relies on `JuMP.set_binary` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
