```
used_by_point_variable(vref::GeneralVariableRef)::Bool
```

Define `used_by_point_variable` for general variable references. It relies on `used_by_point_variable` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
