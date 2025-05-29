```
JuMP.has_lower_bound(vref::GeneralVariableRef)
```

Define `JuMP.has_lower_bound` for general variable references. It relies on `JuMP.has_lower_bound` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
