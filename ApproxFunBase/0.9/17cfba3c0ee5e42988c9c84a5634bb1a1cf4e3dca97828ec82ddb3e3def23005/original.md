```
Derivative()
```

Return the first derivative on an unset space. Spaces will be inferred when applying or manipulating the operator.

# Examples

```jldoctest
julia> Derivative() * Fun(x->x^2) ≈ Fun(x->2x)
true
```
