```
poly_chebyshev2(n, [::Type{T}=Int, [var=:x]])
```

Create a Chebyshev of the second kind  of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_chebyshev2(4)
Polynomials.Polynomial(1 - 12*x^2 + 16*x^4)

julia> p2 = poly_chebyshev2(4, BigInt)
Polynomials.Polynomial(1 - 12*x^2 + 16*x^4)

julia> p3 = poly_chebyshev2(4, Float64, :y)
Polynomials.Polynomial(1.0 - 12.0*y^2 + 16.0*y^4)
```
