```
used_by_derivative(vref::Union{InfiniteVariableRef, DerivativeRef})::Bool
```

Return a `Bool` indicating if `vref` is used by a derivative.

**Example**

```julia-repl
julia> used_by_derivative(vref)
true
```
