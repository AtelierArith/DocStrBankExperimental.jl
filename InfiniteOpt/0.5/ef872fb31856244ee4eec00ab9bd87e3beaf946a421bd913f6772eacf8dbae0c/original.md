```
JuMP.fix_value(vref::GeneralVariableRef)
```

Define `JuMP.fix_value` for general variable references. It relies on `JuMP.fix_value` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
