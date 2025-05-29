```
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Symbol)
```

Generate a cached variant of the [`AbstractManifoldObjective`](@ref) `o` on the `AbstractManifold M` based on the symbol `cache`.

The following caches are available

  * `:Simple` generates a [`SimpleManifoldCachedObjective`](@ref)
  * `:LRU` generates a [`ManifoldCachedObjective`](@ref) where you should use the form `(:LRU, [:Cost, :Gradient])` to specify what should be cached or `(:LRU, [:Cost, :Gradient], 100)` to specify the cache size. Here this variant defaults to `(:LRU, [:Cost, :Gradient], 100)`, caching up to 100 cost and gradient values.[^1]

[^1]: This cache requires [`LRUCache.jl`](https://github.com/JuliaCollections/LRUCache.jl) to be loaded as well.
