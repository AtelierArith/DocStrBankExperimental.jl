```
reset_start_value_functionc(vref::GeneralVariableRef)
```

Define `reset_start_value_function` for general variable references. It relies on `reset_start_value_function` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
