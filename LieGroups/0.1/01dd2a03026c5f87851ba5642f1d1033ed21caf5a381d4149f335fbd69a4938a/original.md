```
exp(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, X)
exp(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, X)
exp!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h, X)
exp!(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h, g, X)
```

Compute the Lie group exponential on a [`LieGroup`](@ref) at a point `g` or the [`Identity`](@ref) with an [`AbelianMultiplicationGroupOperation`](@ref).

Due to differences in the representation of some abelian Lie groups, this method wraps a concrete implementation of a specific abelian LieGroup with inputs of type `AbstractArray{<:Any,0}` and supports in-place computation.

This can be computed in-place of `h` if `h` is `mutable`.
