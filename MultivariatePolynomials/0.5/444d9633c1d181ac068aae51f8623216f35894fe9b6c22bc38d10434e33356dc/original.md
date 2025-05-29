```
map_coefficients(f::Function, p::AbstractPolynomialLike, nonzero = false)
```

Returns a polynomial with the same monomials as `p` but each coefficient `α` is replaced by `f(α)`. The function may return zero in which case the term is dropped. If the function is known to never return zero for a nonzero input, `nonzero` can be set to `true` to get a small speedup.

See also [`map_coefficients!`](@ref) and [`map_coefficients_to!`](@ref).

### Examples

Calling `map_coefficients(α -> mod(3α, 6), 2x*y + 3x + 1)` should return `3x + 3`.
