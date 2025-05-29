```
Derivative(sp::Space, k::Int)
```

Return the `k`-th derivative operator on the space `sp`.

# Examples

```jldoctest
julia> Derivative(Chebyshev(), 2) * Fun(x->x^4) ≈ Fun(x->12x^2)
true
```
