```
Derivative(sp::Space)
```

Return the first derivative operator, equivalent to `Derivative(sp,1)`.

# Examples

```jldoctest
julia> Derivative(Chebyshev()) * Fun(x->x^2) ≈ Fun(x->2x)
true
```
