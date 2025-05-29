```
JuMP.is_integer(vref::GeneralVariableRef)
```

Define `JuMP.is_integer` for general variable references. It relies on `JuMP.is_integer` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
