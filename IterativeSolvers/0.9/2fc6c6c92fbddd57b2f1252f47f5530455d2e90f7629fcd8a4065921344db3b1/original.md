```
chebyshev(A, b, λmin::Real, λmax::Real; kwargs...) -> x, [history]
```

Same as [`chebyshev!`](@ref), but allocates a solution vector `x` initialized with zeros.
