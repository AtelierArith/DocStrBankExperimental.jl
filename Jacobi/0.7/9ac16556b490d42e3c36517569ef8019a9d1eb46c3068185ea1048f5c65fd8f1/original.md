```
poly_dlegendre(n, [::Type{T}=Int, [var=:x]])
```

Create a derivative of Legendre polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_dlegendre(4)
Polynomials.Polynomial(-7.5*x + 17.5*x^3)

julia> p2 = poly_dlegendre(4, Rational{Int})
Polynomials.Polynomial(-15//2*x + 35//2*x^3)

julia> p3 = poly_dlegendre(4, BigFloat, :y)
Polynomials.Polynomial(-7.5*y + 17.5*y^3)
```
