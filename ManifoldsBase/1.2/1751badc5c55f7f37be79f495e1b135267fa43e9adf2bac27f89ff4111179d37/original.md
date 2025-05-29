```
IsEmbeddedSubmanifold <: AbstractTrait
```

A trait to determine whether an [`AbstractDecoratorManifold`](@ref) `M` is an embedded submanifold. It is a special case of the [`IsIsometricEmbeddedManifold`](@ref) trait, i.e. it has all properties of this trait.

In this trait, additionally to the isometric embedded manifold, all retractions, inverse retractions, and vectors transports, especially [`exp`](@ref), [`log`](@ref), and [`parallel_transport_to`](@ref) are passed to the embedding.
