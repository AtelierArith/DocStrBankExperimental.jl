```
primitive_part(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm) where {T}
```

Return the *primitive part* of the polynomial `poly` over a unique factorization domain `S` as defined in [Knu14, (3) p. 423]. That is, return the exact division of `poly` by its [`content`](@ref). If the content is also needed, call [`primitive_part_content`](@ref) instead.

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
