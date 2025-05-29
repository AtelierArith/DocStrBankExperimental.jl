```
JuMP.is_integer(vref::UserDecisionVariableRef)::Bool
```

Extend `JuMP.is_integer` to return `Bool` whether an `InfiniteOpt` variable is  integer.

**Example**

```julia-repl
julia> is_integer(vref)
true
```
