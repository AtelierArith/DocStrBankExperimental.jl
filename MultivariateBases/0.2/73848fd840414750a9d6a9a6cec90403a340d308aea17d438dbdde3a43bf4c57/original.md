```
struct MonomialBasis{MT<:MP.AbstractMonomial, MV<:AbstractVector{MT}} <: AbstractPolynomialBasis
    monomials::MV
end
```

Monomial basis with the monomials of the vector `monomials`. For instance, `MonomialBasis([1, x, y, x^2, x*y, y^2])` is the monomial basis for the subspace of quadratic polynomials in the variables `x`, `y`.

This basis is orthogonal under a scalar product defined with the complex Gaussian measure as density. Once normalized so as to be orthonormal with this scalar product, one get ths [`ScaledMonomialBasis`](@ref).
