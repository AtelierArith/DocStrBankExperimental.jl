```
get_vector(G::AbstractLieGroup, c, B::AbstractBasis; kwargs...)
get_vector(𝔤::LieAlgebra, c, B::AbstractBasis; kwargs...)
get_vector!(G::AbstractLieGroup, X::T, c, B::AbstractBasis; kwargs...)
get_vector!(𝔤::LieAlgebra, X::T, c, B::AbstractBasis; kwargs...)
```

Return the vector corresponding to a set of coefficients in an [`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) of the [`LieAlgebra`](@ref) `𝔤`. Since all tangent vectors are assumed to be represented in the Lie algebra, both signatures are equivalent. The operation can be performed in-place of a tangent vector `X` of type `::T`.

By default this function requires [`identity_element`](@ref)`(G)` and calls the corresponding [`get_vector`](@extref ManifoldsBase :jl:function:`ManifoldsBase.get_vectors`) function of the Riemannian manifold the Lie group is build on.

The inverse operation is [`get_coordinates`](@ref).

# Keyword arguments

  * `tangent_vector_type` specify the tangent vector type to use for the allocating variants.

See also [`hat`](@ref)
