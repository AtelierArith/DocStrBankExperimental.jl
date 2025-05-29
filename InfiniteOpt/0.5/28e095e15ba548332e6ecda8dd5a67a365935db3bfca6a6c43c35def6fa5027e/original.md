```
JuMP.BinaryRef(vref::GeneralVariableRef)
```

Define `JuMP.BinaryRef` for general variable references. It relies on `JuMP.BinaryRef` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
