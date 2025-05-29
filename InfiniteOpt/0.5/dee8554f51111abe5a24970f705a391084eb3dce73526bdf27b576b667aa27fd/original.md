```
fill_in_supports!(prefs; [kwargs...])
```

Define `fill_in_supports!` for general variable references. It relies on `fill_in_supports!` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information. Note that this is a auto generated wrapper and the underlying method may or may not use `kwargs`.
