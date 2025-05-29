```
JuMP.LowerBoundRef(vref::GeneralVariableRef)
```

Define `JuMP.LowerBoundRef` for general variable references. It relies on `JuMP.LowerBoundRef` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
