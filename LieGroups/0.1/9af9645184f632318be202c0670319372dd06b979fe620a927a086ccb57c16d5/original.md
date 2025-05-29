```
inv(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, g)
inv!(G::LieGroup{𝔽,<:AbstractMultiplicationGroupOperation}, h, g)
```

Compute the inverse group element $g^{-1}$, which for the [`AbelianMultiplicationGroupOperation`](@ref) simplifies for a scalar input to the ordinary scalar inverse $g^{-1}$.

Due to differences in the representation of some abelian Lie groups, this method wraps a concrete implementation of a specific abelian LieGroup with inputs of type `AbstractArray{<:Any,0}` and supports in-place computation.

This can be computed in-place of `h` if `h` is `mutable`.
