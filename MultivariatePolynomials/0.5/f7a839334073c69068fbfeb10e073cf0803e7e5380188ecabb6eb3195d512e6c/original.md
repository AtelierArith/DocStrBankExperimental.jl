```
struct Polynomial{CoeffType,T<:AbstractTerm{CoeffType},V<:AbstractVector{T}} <: AbstractPolynomial{CoeffType}
    terms::V
end
```

Representation of a multivariate polynomial as a vector of nonzero terms sorted in ascending monomial order.
