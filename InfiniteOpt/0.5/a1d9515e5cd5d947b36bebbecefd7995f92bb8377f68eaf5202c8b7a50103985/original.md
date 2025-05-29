```
JuMP.fix(vref::GeneralVariableRef, value::Real; force::Bool = false)::Nothing
```

Define `JuMP.fix` for general variable references. It relies on `JuMP.fix` being defined for the underlying `DispatchVariableRef`, otherwise an `ArgumentError` is thrown. See the underlying docstrings for more information.
