```
JuMP.is_integer(vref::SemiInfiniteVariableRef)::Bool
```

Extend `JuMP.is_integer` to return `Bool` whether the original infinite variable of `vref` is integer.

**Example**

```julia-repl
julia> is_integer(vref)
true
```
