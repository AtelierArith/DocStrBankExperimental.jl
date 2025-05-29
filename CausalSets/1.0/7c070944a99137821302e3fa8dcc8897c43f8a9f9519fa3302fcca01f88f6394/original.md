```
AbstractManifold{N}
```

Supertype for `N`-dimensional manifolds. This type specifies the topology, metric and coordinate system of the manifold. (Currently, multiple coordinate systems are not supported).

The manifolds specified by this type themselves are infinitely large, so in order to work with a finite region, you will have to use the [`AbstractBoundary`](@ref) types.
