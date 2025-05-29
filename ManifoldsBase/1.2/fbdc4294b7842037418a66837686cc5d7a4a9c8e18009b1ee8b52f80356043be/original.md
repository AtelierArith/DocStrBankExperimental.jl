```
base_manifold(M::AbstractManifold, depth = Val(-1))
```

Return the internally stored [`AbstractManifold`](@ref) for decorated manifold `M` and the base manifold for vector bundles or power manifolds. The optional parameter `depth` can be used to remove only the first `depth` many decorators and return the [`AbstractManifold`](@ref) from that level, whether its decorated or not. Any negative value deactivates this depth limit.
