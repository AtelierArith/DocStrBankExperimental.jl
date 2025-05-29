```
JuMP.unset_integer(vref::GeneralVariableRef)
```

Define `JuMP.unset_integer` for general variable references. It relies on `JuMP.unset_integer` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
