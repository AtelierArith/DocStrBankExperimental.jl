```
used_by_infinite_variable(vref::GeneralVariableRef)::Bool
```

Define `used_by_infinite_variable` for general variable references. It relies on `used_by_infinite_variable` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
