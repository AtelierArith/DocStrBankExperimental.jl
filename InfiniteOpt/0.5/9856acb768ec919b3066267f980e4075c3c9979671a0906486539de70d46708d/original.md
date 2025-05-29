```
JuMP.is_fixed(vref::UserDecisionVariableRef)::Bool
```

Extend `JuMP.is_fixed` to return `Bool` whether an `InfiniteOpt` variable is  fixed.

**Example**

```julia-repl
julia> is_fixed(vref)
true
```
