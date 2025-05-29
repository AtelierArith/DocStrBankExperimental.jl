```
JuMP.unset_binary(vref::GeneralVariableRef)
```

Define `JuMP.unset_binary` for general variable references. It relies on `JuMP.unset_binary` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
