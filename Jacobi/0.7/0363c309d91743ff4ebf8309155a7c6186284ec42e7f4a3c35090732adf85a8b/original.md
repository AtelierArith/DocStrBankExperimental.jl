```
poly_jacobi(n, [::Type{T}=Int, [var=:x]])
```

Create a Jacobi polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `a` Weight α of the Jacobi polynomial
  * `b` Weight β of the Jacobi polynomial
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_jacobi(4, 1, 1)
Polynomials.Polynomial(0.625 - 8.75*x^2 + 13.125*x^4)

julia> p2 = poly_jacobi(4, 1, 1, Rational{Int})
Polynomials.Polynomial(5//8 - 35//4*x^2 + 105//8*x^4)

julia> p3 = poly_jacobi(4, 1, 1, BigFloat, :y)
Polynomials.Polynomial(0.625 - 8.75*y^2 + 13.125*y^4)
```
