```
log(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, h)
log(G::LieGroup{𝔽,<:AbelianMultiplicationGroupOperation}, g, h)
log!(G::LieGroup{𝔽,<:AbeliantMultiplicationGroupOperation}, X, g)
log!(G::LieGroup{𝔽,<:AbeliantMultiplicationGroupOperation}, X, g, h)
```

Compute the Lie group logarithm on a [`LieGroup`](@ref) at a point `g` or the [`Identity`](@ref) with a concrete instance of [`AbelianMultiplicationGroupOperation`](@ref).

Due to differences in the representation of some abelian Lie groups, this method wraps a concrete implementation of a specific abelian LieGroup with inputs of type `AbstractArray{<:Any,0}` and supports in-place computation.

This can be computed in-place of `X` if `X` is `mutable`.
