```
log(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
log!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, X, g)
```

Compute the Lie group logarithm on a [`LieGroup`](@ref) with a concrete instance of [`AbstractMultiplicationGroupOperation`](@ref), which simplifies to the [(matrix) logarithm](https://en.wikipedia.org/wiki/Logarithm_of_a_matrix).

This can be computed in-place of `X`.
