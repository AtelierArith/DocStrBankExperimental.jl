```
used_by_objective(vref::GeneralVariableRef)::Bool
```

Define `used_by_objective` for general variable references. It relies on `used_by_objective` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
