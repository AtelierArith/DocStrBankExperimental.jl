```
parameter_refs(expr)::Tuple
```

Return the tuple of parameter references that determine the infinite dependencies of `expr`.

**Example**

```julia-repl
julia> parameter_refs(my_expr)
(t,)
```
