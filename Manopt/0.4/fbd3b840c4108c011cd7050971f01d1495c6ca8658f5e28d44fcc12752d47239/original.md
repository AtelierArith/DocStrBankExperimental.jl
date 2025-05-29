```
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Tuple{Symbol, Array, Array})
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Tuple{Symbol, Array})
```

Generate a cached variant of the [`AbstractManifoldObjective`](@ref) `o` on the `AbstractManifold M` based on the symbol `cache[1]`, where the second element `cache[2]` are further arguments to the cache and the optional third is passed down as keyword arguments.

For all available caches see the simpler variant with symbols.
