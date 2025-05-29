```
JuMP.upper_bound(vref::GeneralVariableRef)
```

Define `JuMP.upper_bound` for general variable references. It relies on `JuMP.upper_bound` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
