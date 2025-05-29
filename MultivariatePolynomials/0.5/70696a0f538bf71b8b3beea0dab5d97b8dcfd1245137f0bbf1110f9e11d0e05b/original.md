```
multiplication_preserves_monomial_order(P::Type{<:AbstractPolynomialLike})
```

Returns a `Bool` indicating whether the order is preserved in the multiplication of monomials of type `monomial_type(P)`. That is, if `a < b` then `a * c < b * c` for any monomial `c`. This returns `true` by default. This is used by [`Polynomial`](@ref) so a monomial type for which the multiplication does not preserve the monomial order can still be used with [`Polynomial`](@ref) if it implements a method for this function that returns `false`.
