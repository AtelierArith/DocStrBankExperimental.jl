```
ProcessResultCache(params::AbstractImageReconstructionParameters; maxsize = 1, kwargs...)
```

Cache of size `maxsize` for the result of `process` methods. The cache is based on the `hash` of the inputs of the `process` function. Cache is shared between all algorithms constructed from the same plan. The cache is transparent for properties of the underlying parameter. Cache can be invalidated by calling `empty!` on the cache.
