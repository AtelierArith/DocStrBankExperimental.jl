```
used_by_parameter_function(vref::GeneralVariableRef)::Bool
```

Define `used_by_parameter_function` for general variable references. It relies on `used_by_parameter_function` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
