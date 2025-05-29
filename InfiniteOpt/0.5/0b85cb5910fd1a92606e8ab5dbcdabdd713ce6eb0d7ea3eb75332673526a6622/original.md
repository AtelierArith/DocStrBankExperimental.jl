```
JuMP.set_value(vref::DispatchVariableRef, value::Real)::Nothing
```

Extend `JuMP.set_value` to set the value of `vref`. It relies on `JuMP.set_value` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown.
