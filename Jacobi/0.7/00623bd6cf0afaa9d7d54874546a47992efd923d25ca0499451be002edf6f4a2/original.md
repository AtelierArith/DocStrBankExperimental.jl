```
poly_chebyshev(n, [::Type{T}=Int, [var=:x]])
```

Create a Chebyshev polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_chebyshev(4)
Polynomials.Polynomial(1 - 8*x^2 + 8*x^4)

julia> p2 = poly_chebyshev(4, BigInt)
Polynomials.Polynomial(1 - 8*x^2 + 8*x^4)

julia> p3 = poly_chebyshev(4, Float64, :y)
Polynomials.Polynomial(1.0 - 8.0*y^2 + 8.0*y^4)

```
