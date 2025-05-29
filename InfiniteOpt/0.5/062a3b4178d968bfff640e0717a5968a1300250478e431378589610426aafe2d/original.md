```
eval_supportsc(vref::GeneralVariableRef)
```

Define `eval_supports` for general variable references. It relies on `eval_supports` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
