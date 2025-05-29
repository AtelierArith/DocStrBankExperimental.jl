```
JuMP.has_lower_bound(vref::UserDecisionVariableRef)::Bool
```

Extend `JuMP.has_lower_bound` to return a `Bool` whether an `InfiniteOpt`  variable has a lower bound.

**Example**

```julia-repl
julia> has_lower_bound(vref)
true
```
