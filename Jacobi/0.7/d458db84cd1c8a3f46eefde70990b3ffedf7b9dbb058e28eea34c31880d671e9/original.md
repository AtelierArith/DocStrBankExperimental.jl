```
poly_legendre(n, [::Type{T}=Int, [var=:x]])
```

Create a Legendre polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_legendre(4)
Polynomials.Polynomial(0.375 - 3.75*x^2 + 4.375*x^4)

julia> p2 = poly_legendre(4, Rational{Int})
Polynomials.Polynomial(3//8 - 15//4*x^2 + 35//8*x^4)

julia> p3 = poly_legendre(4, BigFloat, :y)
Polynomials.Polynomial(0.375 - 3.75*y^2 + 4.375*y^4)
```
