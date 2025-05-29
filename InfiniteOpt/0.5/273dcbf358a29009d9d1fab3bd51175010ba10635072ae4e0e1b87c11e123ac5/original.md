```
JuMP.is_binary(vref::GeneralVariableRef)
```

Define `JuMP.is_binary` for general variable references. It relies on `JuMP.is_binary` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
