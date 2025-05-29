```
start_value(v::VariableRef)
```

Return the start value (MOI attribute `VariablePrimalStart`) of the variable `v`.

Note: `VariablePrimalStart`s are sometimes called "MIP-starts" or "warmstarts".

See also [`set_start_value`](@ref).
