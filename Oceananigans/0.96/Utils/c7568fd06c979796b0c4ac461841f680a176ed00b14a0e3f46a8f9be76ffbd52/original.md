```
@apply_regionally expr
```

Distributes locally the function calls in `expr`ession

It calls [`apply_regionally!`](@ref) when the functions do not return anything.

In case the function in `expr` returns something, `@apply_regionally` calls [`construct_regionally`](@ref).
