```
JuMP.unfix(vref::GeneralVariableRef)
```

Define `JuMP.unfix` for general variable references. It relies on `JuMP.unfix` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
