```
DefaultLieAlgebraOrthogonalBasis{𝔽} <: ManifoldsBase.AbstractOrthogonalBasis{𝔽,ManifoldsBase.TangentSpaceType}
```

Specify an orthogonal basis for a Lie algebra. This is used as the default within [`hat`](@ref) and [`vee`](@ref).

If not specifically overwritten/implemented for a Lie group, the [`DefaultOrthogonalBasis`](@extref `ManifoldsBase.DefaultOrthogonalBasis`) at the [`identity_element`](@ref) on the [`base_manifold](@ref base_manifold(::AbstractLieGroup)) acts as a fallback.

!!! note
    In order to implement the corresponding [`get_coordinates`](@ref) and [`get_vector`](@ref) functions, define `get_coordinates_lie(::AbstractLieAlgebra, X, B)` and `get_vector_lie(::AbstractLieAlgebra, X, B)`, resp.

