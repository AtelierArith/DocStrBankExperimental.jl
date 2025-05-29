```
gmres(A, b; kwargs...) -> x, [history]
```

Same as [`gmres!`](@ref), but allocates a solution vector `x` initialized with zeros.
