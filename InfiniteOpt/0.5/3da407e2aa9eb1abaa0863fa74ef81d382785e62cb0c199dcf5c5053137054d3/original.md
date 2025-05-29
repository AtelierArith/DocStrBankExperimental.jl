```
JuMP.has_upper_bound(vref::UserDecisionVariableRef)::Bool
```

Extend `JuMP.has_upper_bound` to return a `Bool` whether an `InfiniteOpt`  variable has an upper bound.

**Example**

```julia-repl
julia> has_upper_bound(vref)
true
```
