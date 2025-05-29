```
AbstractDecoratorManifold{𝔽} <: AbstractManifold{𝔽}
```

Declare a manifold to be an abstract decorator. A manifold which is a subtype of is a **decorated manifold**, i.e. has

  * certain additional properties or
  * delegates certain properties to other manifolds.

Most prominently, a manifold might be an embedded manifold, i.e. points on a manifold $\mathcal M$ are represented by (some, maybe not all) points on another manifold $\mathcal N$. Depending on the type of embedding, several functions are dedicated to the embedding. For example if the embedding is isometric, then the [`inner`](@ref) does not have to be implemented for $\mathcal M$ but can be automatically implemented by deligation to $\mathcal N$.

This is modelled by the `AbstractDecoratorManifold` and traits. These are mapped to functions, which determine the types of transparencies.
