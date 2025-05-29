```
JuMP.is_fixed(vref::GeneralVariableRef)
```

Define `JuMP.is_fixed` for general variable references. It relies on `JuMP.is_fixed` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
