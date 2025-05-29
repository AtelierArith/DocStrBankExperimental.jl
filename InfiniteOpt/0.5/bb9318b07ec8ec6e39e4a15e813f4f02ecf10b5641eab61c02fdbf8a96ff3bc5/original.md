```
parameter_refs(cref::InfOptConstraintRef)::Tuple
```

Return the tuple of infinite parameter references that determine the infinite dependencies of `cref`.

**Example**

```julia-repl
julia> parameter_refs(cref)
(t,)
```
