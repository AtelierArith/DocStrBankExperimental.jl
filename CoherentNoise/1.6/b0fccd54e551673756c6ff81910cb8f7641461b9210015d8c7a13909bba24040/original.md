```
cache(x::AbstractSampler)
```

Construct a modifier sampler that caches the set of the input coordinates and their corresponding output value of its source sampler. If the input coordinates differs from the previously cached output, the cache is invalidated and the new output is cached.

Caching is useful if a sampler is used as a source for multiple modifiers. Without caching, the duplicated input sources would redundantly compute the same outputs, which would be expensive, especially if long pipelines share a long subgraph.
