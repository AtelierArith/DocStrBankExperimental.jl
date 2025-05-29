```
infinite_variable_refc(vref::GeneralVariableRef)
```

Define `infinite_variable_ref` for general variable references. It relies on `infinite_variable_ref` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
