```
JuMP.IntegerRef(vref::GeneralVariableRef)
```

Define `JuMP.IntegerRef` for general variable references. It relies on `JuMP.IntegerRef` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
