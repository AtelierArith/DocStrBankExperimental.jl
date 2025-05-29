```
LaurentPolynomial{T,X}(coeffs::AbstractVector, [m::Integer = 0], [var = :x])
```

A [Laurent](https://en.wikipedia.org/wiki/Laurent_polynomial) polynomial is of the form `a_{m}x^m + ... + a_{n}x^n` where `m,n` are  integers (not necessarily positive) with `m <= n`.

The `coeffs` specify `a_{m}, a_{m-1}, ..., a_{n}`. The argument `m` represents the lowest exponent of the variable in the series, and is taken to be zero by default.

Laurent polynomials and standard basis polynomials promote to  Laurent polynomials. Laurent polynomials may be  converted to a standard basis  polynomial when `m >= 0`,

Integration will fail if there is a `x⁻¹` term in the polynomial.

!!! note
    `LaurentPolynomial` is axis-aware, unlike the other polynomial types in this package.


# Examples:

```jldoctest
julia> using Polynomials

julia> P = LaurentPolynomial;

julia> p = P([1,1,1],  -1)
LaurentPolynomial(x⁻¹ + 1 + x)

julia> q = P([1,1,1])
LaurentPolynomial(1 + x + x²)

julia> pp = Polynomial([1,1,1])
Polynomial(1 + x + x^2)

julia> p + q
LaurentPolynomial(x⁻¹ + 2 + 2*x + x²)

julia> p * q
LaurentPolynomial(x⁻¹ + 2 + 3*x + 2*x² + x³)

julia> p * pp
LaurentPolynomial(x⁻¹ + 2 + 3*x + 2*x² + x³)

julia> pp - q
LaurentPolynomial(0)

julia> derivative(p)
LaurentPolynomial(-x⁻² + 1)

julia> integrate(q)
LaurentPolynomial(1.0*x + 0.5*x² + 0.3333333333333333*x³)

julia> integrate(p)  # x⁻¹  term is an issue
ERROR: ArgumentError: Can't integrate Laurent polynomial with  `x⁻¹` term
[...]

julia> integrate(P([1,1,1], -5))
LaurentPolynomial(-0.25*x⁻⁴ - 0.3333333333333333*x⁻³ - 0.5*x⁻²)

julia> x⁻¹ = inv(variable(LaurentPolynomial)) # `inv` defined on monomials
LaurentPolynomial(1.0*x⁻¹)

julia> p = Polynomial([1,2,3])
Polynomial(1 + 2*x + 3*x^2)

julia> x = variable()
Polynomial(x)

julia> x^degree(p) * p(x⁻¹) # reverses  coefficients
LaurentPolynomial(3.0 + 2.0*x + 1.0*x²)
```
