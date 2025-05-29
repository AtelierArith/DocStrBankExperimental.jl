```
IsIsometricManifoldEmbeddedManifold <: AbstractTrait
```

A Trait to determine whether an [`AbstractDecoratorManifold`](@ref) `M` is an isometrically embedded manifold. It is a special case of the [`IsEmbeddedManifold`](@ref) trait, i.e. it has all properties of this trait.

Here, additionally, netric related functions like [`inner`](@ref) and [`norm`](@ref) are passed to the embedding
