```
constant_monomial(p::AbstractPolynomialLike)
```

Returns a constant monomial of the monomial type of `p` with the same variables as `p`.

```
constant_monomial(::Type{PT}) where {PT<:AbstractPolynomialLike}
```

Returns a constant monomial of the monomial type of a polynomial of type `PT`.
