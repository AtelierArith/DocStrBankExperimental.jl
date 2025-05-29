```
has_derivative_constraints(vref::GeneralVariableRef)::Bool
```

Define `has_derivative_constraints` for general variable references. It relies on `has_derivative_constraints` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
