```
poly_dchebyshev(n, [::Type{T}=Int, [var=:x]])
```

Create the derivative of Chebyshev polynomial of order n `Polynomial` object.

Instead of computing the polynomial at a specific point,  use `Polynomials` package to compute the actual polynomial

Parameters:

  * `n` Order of polynomials
  * `T` Type of polynomial coefficients
  * `var` symbol to be used as variable by the polynomial

# Examples

```julia-repl
julia> p = poly_dchebyshev(4)
Polynomials.Polynomial(-16*x + 32*x^3)

julia> p2 = poly_dchebyshev(4, BigInt)
Polynomials.Polynomial(-16*x + 32*x^3)

julia> p3 = poly_dchebyshev(4, Float64, :y)
Polynomials.Polynomial(-16.0*y + 32.0*y^3)
```
