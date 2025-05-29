```
EmbeddedManifold{𝔽, MT <: AbstractManifold, NT <: AbstractManifold} <: AbstractDecoratorManifold{𝔽}
```

A type to represent an explicit embedding of a [`AbstractManifold`](@ref) `M` of type `MT` embedded into a manifold `N` of type `NT`. By default, an embedded manifold is set to be embedded, but neither isometrically embedded nor a submanifold.

!!! note
    This type is not required if a manifold `M` is to be embedded in one specific manifold `N`.  One can then just implement [`embed!`](@ref) and [`project!`](@ref). You can further pass functions to the embedding, for example, when it is an isometric embedding, by using an [`AbstractDecoratorManifold`](@ref). Only for a second –maybe considered non-default– embedding, this type should be considered in order to dispatch on different embed and project methods for different embeddings `N`.


# Fields

  * `manifold` the manifold that is an embedded manifold
  * `embedding` a second manifold, the first one is embedded into

# Constructor

```
EmbeddedManifold(M, N)
```

Generate the `EmbeddedManifold` of the [`AbstractManifold`](@ref) `M` into the [`AbstractManifold`](@ref) `N`.
