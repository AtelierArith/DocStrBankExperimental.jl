```
struct FixedPolynomialBasis{PT<:MP.AbstractPolynomialLike, PV<:AbstractVector{PT}} <: AbstractPolynomialBasis
    polynomials::PV
end
```

Polynomial basis with the polynomials of the vector `polynomials`. For instance, `FixedPolynomialBasis([1, x, 2x^2-1, 4x^3-3x])` is the Chebyshev polynomial basis for cubic polynomials in the variable `x`.
