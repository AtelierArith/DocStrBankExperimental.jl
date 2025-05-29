```
JuMP.is_fixed(vref::SemiInfiniteVariableRef)::Bool
```

Extend `JuMP.is_fixed` to return `Bool` whether the original infinite variable of `vref` is fixed.

**Example**

```julia-repl
julia> is_fixed(vref)
true
```
