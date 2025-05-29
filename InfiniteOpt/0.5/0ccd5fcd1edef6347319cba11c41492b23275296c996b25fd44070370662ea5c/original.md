```
is_used(vref::GeneralVariableRef)::Bool
```

Define `is_used` for general variable references. It relies on `is_used` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
