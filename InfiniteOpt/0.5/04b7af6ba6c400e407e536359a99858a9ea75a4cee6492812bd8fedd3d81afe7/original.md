```
JuMP.start_value(vref::GeneralVariableRef)
```

Define `JuMP.start_value` for general variable references. It relies on `JuMP.start_value` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
