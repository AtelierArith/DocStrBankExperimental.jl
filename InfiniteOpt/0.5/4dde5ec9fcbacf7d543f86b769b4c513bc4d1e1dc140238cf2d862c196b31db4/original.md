```
used_by_measure(vref::GeneralVariableRef)::Bool
```

Define `used_by_measure` for general variable references. It relies on `used_by_measure` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
