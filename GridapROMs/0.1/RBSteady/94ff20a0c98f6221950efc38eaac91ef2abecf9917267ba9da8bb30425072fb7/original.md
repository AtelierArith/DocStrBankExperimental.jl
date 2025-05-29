```
abstract type ReducedProjection{A<:AbstractArray} <: Projection end
```

Type representing a Galerkin projection of a [`Projection`](@ref) onto a reduced subspace represented by another `Projection`.

Subtypes:

  * [`ReducedAlgebraicProjection`](@ref)
