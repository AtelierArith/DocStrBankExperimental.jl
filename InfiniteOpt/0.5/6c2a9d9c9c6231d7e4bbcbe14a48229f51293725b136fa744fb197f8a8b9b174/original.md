```
JuMP.lower_bound(vref::SemiInfiniteVariableRef)::Float64
```

Extend `JuMP.lower_bound` to return the lower bound of the original infinite variable of `vref`. Errors if `vref` doesn't have a lower bound.

**Example**

```julia-repl
julia> lower_bound(vref)
0.0
```
