```
identity_element(G::LieGroup{𝔽,AbelianMultiplicationGroupOperation})
identity_element!(G::LieGroup{𝔽,AbelianMultiplicationGroupOperation}, e)
```

Return the point representation of the [`Identity`](@ref), which for an [`AbelianMultiplicationGroupOperation`](@ref) is the one-element.

This can be computed in `e` if `e` is `mutable`.
