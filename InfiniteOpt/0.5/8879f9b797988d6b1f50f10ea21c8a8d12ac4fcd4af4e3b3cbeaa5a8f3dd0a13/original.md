```
is_used(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

Return a `Bool` indicating if `vref` is used in the model.

**Example**

```julia-repl
julia> is_used(vref)
false
```
