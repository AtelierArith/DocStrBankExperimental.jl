```
struct Term{CoeffType,M<:AbstractMonomial} <: AbstractTerm{CoeffType}
    coefficient::CoeffType
    monomial::M
end
```

A representation of the multiplication between a `coefficient` and a `monomial`.

!!! note
    The `coefficient` does not need to be a `Number`. It can be for instance a multivariate polynomial. When computing a multivariate `gcd`, it is actually reformulated as a univariate `gcd` in one of the variable with coefficients being multivariate polynomials in the other variables. To create such a term, use [`term`](@ref) instead of `*`. For instance, if `p` is a polynomial and `m` is a monomial, `p * m` will multiply each term of `p` with `m` but `term(p, m)` will create a term with `p` as coefficient and `m` as monomial.

