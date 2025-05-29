```
used_by_point_variable(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

Return a `Bool` indicating if `vref` is used by a point variable.

**Example**

```julia-repl
julia> used_by_point_variable(vref)
false
```
