```
lazified_conditional_gradient(f, grad!, lmo_base, x0; ...)
```

Similar to [`FrankWolfe.frank_wolfe`](@ref) but lazyfying the LMO: each call is stored in a cache, which is looked up first for a good-enough direction. The cache used is a [`FrankWolfe.MultiCacheLMO`](@ref) or a [`FrankWolfe.VectorCacheLMO`](@ref) depending on whether the provided `cache_size` option is finite.
