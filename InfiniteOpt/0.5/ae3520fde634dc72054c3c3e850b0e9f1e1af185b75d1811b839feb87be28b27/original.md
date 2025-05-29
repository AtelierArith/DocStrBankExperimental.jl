```
JuMP.set_integer(vref::GeneralVariableRef)
```

Define `JuMP.set_integer` for general variable references. It relies on `JuMP.set_integer` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
