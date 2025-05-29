```
used_by_derivative(vref::GeneralVariableRef)::Bool
```

Define `used_by_derivative` for general variable references. It relies on `used_by_derivative` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
