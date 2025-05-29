```
identity_element(G::AbstractLieGroup)
identity_element(G::AbstractLieGroup, T)
identity_element!(G::AbstractLieGroup, e::T)
```

Return a point representation of the [`Identity`](@ref) on the [`AbstractLieGroup`](@ref) `G`. By default this representation is the default array or number representation. If there exist several representations, the type `T` can be used to distinguish between them, and it should be provided for both the [`AbstractLieGroupPoint`](@ref) as well as the [`AbstractLieAlgebraTangentVector`](@ref) if they differ, since maybe only one of these types might be available for the second signature.

It returns the corresponding default representation of $e$ as a point on `G`. This can be performed in-place of `e`.
