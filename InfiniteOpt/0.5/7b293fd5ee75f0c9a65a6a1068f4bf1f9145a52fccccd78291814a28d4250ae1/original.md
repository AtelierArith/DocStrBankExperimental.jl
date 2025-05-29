```
JuMP.index(cref::InfOptConstraintRef)::InfOptConstraintIndex
```

Extend `JuMP.index` to return the index of an `InfiniteOpt` constraint `cref`.

**Example**

```julia-repl
julia> index(cref)
InfOptConstraintIndex(2)
```
