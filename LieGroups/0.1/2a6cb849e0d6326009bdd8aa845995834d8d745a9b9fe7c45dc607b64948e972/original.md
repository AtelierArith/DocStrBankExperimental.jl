```
get_coordinates(𝔤::LieAlgebra, X::T, B::AbstractBasis)
get_coordinates!(𝔤::LieAlgebra, c, X::T, B::AbstractBasis)
```

Return the vector of coordinates to the decomposition of `X` with respect to an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) of the [`LieAlgebra`](@ref) `𝔤`. The operation can be performed in-place of `c`.

By default this function requires that [`identity_element`](@ref)`(G, T)` is available and calls the corresponding [`get_coordinates`](@extref ManifoldsBase :jl:function:`ManifoldsBase.get_coordinates`) function of the Riemannian manifold the Lie group is build on.

The inverse operation is [`get_vector`](@ref).

See also [`vee`](@ref).
