```
JuMP.is_binary(vref::SemiInfiniteVariableRef)::Bool
```

Extend `JuMP.is_binary` to return `Bool` whether the original infinite variable of `vref` is binary.

**Example**

```julia-repl
julia> is_binary(vref)
true
```
