```
used_by_semi_infinite_variable(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

Return a `Bool` indicating if `vref` is used by a semi-infinite variable.

**Example**

```julia-repl
julia> used_by_semi_infinite_variable(vref)
false
```
