```
inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g)
```

Compute the inverse group element $g^{-1}$, which for an [`AbstractMultiplicationGroupOperation`](@ref) simplifies to the multiplicative inverse $g^{-1}$. This can be done in-place of `h`.
