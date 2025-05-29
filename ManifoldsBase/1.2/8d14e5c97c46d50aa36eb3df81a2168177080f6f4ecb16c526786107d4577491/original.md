```
get_embedding(M::AbstractDecoratorManifold)
get_embedding(M::AbstractDecoratorManifold, p)
```

Specify the embedding of a manifold that has abstract decorators. the embedding might depend on a point representation, where different point representations are distinguished as subtypes of [`AbstractManifoldPoint`](@ref). A unique or default representation might also just be an `AbstractArray`.
