```
JuMP.set_start_value(vref::GeneralVariableRef, value::Real)::Nothing
```

Define `JuMP.set_start_value` for general variable references. It relies on `JuMP.set_start_value` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
