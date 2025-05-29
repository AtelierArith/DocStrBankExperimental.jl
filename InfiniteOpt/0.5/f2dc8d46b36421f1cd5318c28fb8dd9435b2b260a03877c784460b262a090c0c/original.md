```
used_by_constraint(vref::GeneralVariableRef)::Bool
```

Define `used_by_constraint` for general variable references. It relies on `used_by_constraint` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
