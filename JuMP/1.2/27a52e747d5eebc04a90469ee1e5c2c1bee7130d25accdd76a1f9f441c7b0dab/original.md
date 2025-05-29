```
set_start_value(variable::VariableRef, value::Union{Real,Nothing})
```

Set the start value (MOI attribute `VariablePrimalStart`) of the `variable` to `value`.

Pass `nothing` to unset the start value.

Note: `VariablePrimalStart`s are sometimes called "MIP-starts" or "warmstarts".

See also [`start_value`](@ref).
