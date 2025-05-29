```
JuMP.fix_value(vref::SemiInfiniteVariableRef)::Float64
```

Extend `JuMP.fix_value` to return the fix value of the original infinite variable of `vref`. Errors if variable is not fixed.

**Example**

```julia-repl
julia> fix_value(vref)
0.0
```
