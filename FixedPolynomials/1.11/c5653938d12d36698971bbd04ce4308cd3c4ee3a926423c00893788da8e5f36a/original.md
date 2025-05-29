```
Polynomial(p::MultivariatePolynomials.AbstractPolynomial [, variables [, homogenized=false]])
```

A structure for fast evaluation of multivariate polynomials. The terms are sorted first by total degree, then lexicographically. `Polynomial` has first class support for [homogenous polynomials](https://en.wikipedia.org/wiki/Homogeneous_polynomial). This field indicates whether the first variable should be considered as the homogenization variable.

```
Polynomial{T}(p::MultivariatePolynomials.AbstractPolynomial [, variables [, homogenized=false]])
```

You can force a coefficient type `T`. For optimal performance `T` should be same type as the input to with which it will be evaluated.

```
Polynomial(exponents::Matrix{Int}, coefficients::Vector{T}, variables, [, homogenized=false])
```

You can also create a polynomial directly. Note that in exponents each column represents the exponent of a term.

### Example

```
Poly([3 1; 1 1; 0 2 ], [-2.0, 3.0], [:x, :y, :z]) == 3.0x^2yz^2 - 2x^3y
```
