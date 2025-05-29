```
evaluate(coefficients::AbstractVector, sp::Space, x)
```

Evaluate the expansion at a point `x` that lies in `domain(sp)`. If `x` is not in the domain, the returned value will depend on the space, and should not be relied upon. See [`extrapolate`](@ref) to evaluate a function at a value outside the domain.
