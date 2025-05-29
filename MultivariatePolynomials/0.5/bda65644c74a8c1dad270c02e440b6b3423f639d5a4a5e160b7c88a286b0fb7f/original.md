```
map_coefficients!(f::Function, p::AbstractPolynomialLike, nonzero = false)
```

Mutate `p` by replacing each coefficient `α` by `f(α)`. The function may return zero in which case the term is dropped. If the function is known to never return zero for a nonzero input, `nonzero` can be set to `true` to get a small speedup. The function returns `p`, which is identically equal to the second argument.

See also [`map_coefficients`](@ref) and [`map_coefficients_to!`](@ref).

### Examples

Let `p = 2x*y + 3x + 1`, after `map_coefficients!(α -> mod(3α, 6), p)`, `p` is equal to `3x + 3`.
