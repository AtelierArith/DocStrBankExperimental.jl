```
content(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm, mutability::MA.MutableTrait) where {T}
```

Return the *content* of the polynomial `poly` over a unique factorization domain `S` as defined in [Knu14, (3) p. 423]. That is, return the `gcd` of the coefficients of `poly`. See also [`primitive_part_content`](@ref).

The output can be mutated without affecting `poly` if `mutability` is `MA.IsNotMutable`.

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
