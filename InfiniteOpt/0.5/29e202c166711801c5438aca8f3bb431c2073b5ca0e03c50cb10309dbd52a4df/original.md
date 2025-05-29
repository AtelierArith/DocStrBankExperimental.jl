```
JuMP.set_upper_bound(vref::GeneralVariableRef, value::Real)::Nothing
```

Define `JuMP.set_upper_bound` for general variable references. It relies on `JuMP.set_upper_bound` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
