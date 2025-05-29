```
primitive_part_content(poly::AbstractPolynomialLike{T}, algo::AbstractUnivariateGCDAlgorithm) where {T}
```

Return the *primitive part* and *content* of the polynomial `poly` over a unique factorization domain `S` as defined in [Knu14, (3) p. 423]. This is more efficient to call this function rather than calling [`primitive_part`](@ref) and [`content`](@ref) separately since computing the primitive part requires computing the content first and this function avoid computing the content twice.

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
