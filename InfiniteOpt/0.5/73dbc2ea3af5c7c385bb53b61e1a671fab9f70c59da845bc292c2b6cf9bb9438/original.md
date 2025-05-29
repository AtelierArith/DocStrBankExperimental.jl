```
JuMP.has_lower_bound(vref::SemiInfiniteVariableRef)::Bool
```

Extend `JuMP.has_lower_bound` to return a `Bool` whether the original infinite variable of `vref` has a lower bound.

**Example**

```julia-repl
julia> has_lower_bound(vref)
true
```
