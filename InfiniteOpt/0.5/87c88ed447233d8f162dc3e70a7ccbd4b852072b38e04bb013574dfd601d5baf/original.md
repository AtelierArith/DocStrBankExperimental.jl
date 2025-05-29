```
JuMP.has_upper_bound(vref::SemiInfiniteVariableRef)::Bool
```

Extend `JuMP.has_upper_bound` to return a `Bool` whether the original infinite variable of `vref` has an upper bound.

**Example**

```julia-repl
julia> has_upper_bound(vref)
true
```
