```
abstract type Projection <: Map end
```

Represents a basis for a `n`-dimensional vector subspace of a `N`-dimensional vector space (where `N >> n`), to be used as a Galerkin projection operator. The kernel of a Projection is `n`-dimensional, whereas its image is `N`-dimensional.

Subtypes:

  * [`PODProjection`](@ref)
  * [`TTSVDProjection`](@ref)
  * [`NormedProjection`](@ref)
  * [`BlockProjection`](@ref)
  * [`InvProjection`](@ref)
  * [`ReducedProjection`](@ref)
  * [`HyperReduction`](@ref)
