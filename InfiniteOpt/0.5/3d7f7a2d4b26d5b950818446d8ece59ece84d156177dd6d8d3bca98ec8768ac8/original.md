```
JuMP.fix(vref::UserDecisionVariableRef, value::Real;
         force::Bool = false)::Nothing
```

Extend `JuMP.fix` to fix the value of an `InfiniteOpt` variable. Errors if  variable has a lower and/or an upper bound(s) unless `force = true`.

**Examples**

```julia-repl
julia> fix(vref, 3)

julia> fix_value(vref)
3.0

julia> fix(vref2, 2, force = true)

julia> fix_value(vref2)
2.0
```
