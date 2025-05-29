```
poly_djacobi(n, [::Type{T}=Int, [var=:x]])
```

Create a derivative of Jacobi polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `a` Weight α of the Jacobi polynomial
  * `b` Weight β of the Jacobi polynomial
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_djacobi(4, 1, 1)
Polynomials.Polynomial(-17.5*x + 52.5*x^3)

julia> p2 = poly_djacobi(4, 1, 1, Rational{Int})
Polynomials.Polynomial(-35//2*x + 105//2*x^3)

julia> p3 = poly_djacobi(4, 1, 1, BigFloat, :y)
Polynomials.Polynomial(-17.5*y + 52.5*y^3)
```
