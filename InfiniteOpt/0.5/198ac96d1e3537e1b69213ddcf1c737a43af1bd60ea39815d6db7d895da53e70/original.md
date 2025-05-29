```
derivative_method(prefs; [kwargs...])
```

Define `derivative_method` for general variable references. It relies on `derivative_method` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information. Note that this is a auto generated wrapper and the underlying method may or may not use `kwargs`.
