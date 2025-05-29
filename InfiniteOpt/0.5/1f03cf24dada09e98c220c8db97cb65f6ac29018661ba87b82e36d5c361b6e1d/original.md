```
JuMP.fix_value(vref::UserDecisionVariableRef)::Float64
```

Extend `JuMP.fix_value` to return the fix value of an `InfiniteOpt` variable.  Errors if variable is not fixed.

**Example**

```julia-repl
julia> fix_value(vref)
0.0
```
