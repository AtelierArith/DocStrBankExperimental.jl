```
substitute(p::Polynomial, expr::Expr)
(→)(p::Polynomial, expr::Expr)
```

Substitutes `expr` for `p.variable`. `expr` can be only `√x`, `a*x^b` or `√(a*x^b)`.

# Examples

```julia
julia> p = Polynomial([1, 2, 3, 4, 5], [-2, -1, 0, 1, 2])
z^-2 + 2*z^-1 + 3 + 4*z + 5*z^2

julia> substitute(p, :(√x))
x^-1 + 2*x^⁻¹/₂ + 3 + 4*x^¹/₂ + 5*x

julia> :(√x) → p
x^-1 + 2*x^⁻¹/₂ + 3 + 4*x^¹/₂ + 5*x
```
