```
JuMP.UpperBoundRef(vref::GeneralVariableRef)
```

Define `JuMP.UpperBoundRef` for general variable references. It relies on `JuMP.UpperBoundRef` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
