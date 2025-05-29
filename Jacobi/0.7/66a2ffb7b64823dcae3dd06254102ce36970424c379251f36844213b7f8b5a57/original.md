```
poly_dchebyshev2(n, [::Type{T}=Int, [var=:x]])
```

Create a derivative of Chebyshev polynomial of the second kind  of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_dchebyshev2(4)
Polynomials.Polynomial(-24*x + 64*x^3)

julia> p2 = poly_dchebyshev2(4, BigInt)
Polynomials.Polynomial(-24*x + 64*x^3)

julia> p3 = poly_dchebyshev2(4, Float64, :y)
Polynomials.Polynomial(-24.0*y + 64.0*y^3)
```
