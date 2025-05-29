```
set_start_value_function(vref::GeneralVariableRef, start::Union{Real, Function})::Nothing
```

Set the start value function of `vref`. It relies on `set_start_value_function` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown.
