```
compose(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, h)
compose!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, k, g, h)
```

Compute the group operation composition of `g` and `h` with respect to an [`AbstractMultiplicationGroupOperation`](@ref) on an [`LieGroup`](@ref) `G`, which falls back to calling `g*h`, where `*` is assumed to be overloaded accordingly.

This can be computed in-place of `k`.
