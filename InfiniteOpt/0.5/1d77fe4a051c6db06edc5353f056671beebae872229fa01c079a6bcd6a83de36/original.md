```
JuMP.FixRef(vref::GeneralVariableRef)
```

Define `JuMP.FixRef` for general variable references. It relies on `JuMP.FixRef` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
