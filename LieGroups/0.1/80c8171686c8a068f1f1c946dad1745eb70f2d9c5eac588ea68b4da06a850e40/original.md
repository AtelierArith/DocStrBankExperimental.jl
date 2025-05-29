```
exp(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, X)
exp!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g, X)
```

Compute the Lie group exponential on a [`LieGroup`](@ref) with an [`AbstractMultiplicationGroupOperation`](@ref), which simplifies to the [matrix exponential](https://en.wikipedia.org/wiki/Matrix_exponential).

This can be computed in-place of `g`.
