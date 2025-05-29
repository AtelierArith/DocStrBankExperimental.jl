```
CachedDataset(source, cachesize = numbobs(source))
CachedDataset(source, cacheidx = 1:numbobs(source))
CachedDataset(source, cacheidx, cache)
```

Wrap a `source` data container and cache `cachesize` samples in memory. This can be useful for improving read speeds when `source` is a lazy data container, but your system memory is large enough to store a sizeable chunk of it.

By default the observation indices `1:cachesize` are cached. You can manually pass in a set of `cacheidx` as well.

See also [`make_cache`](@ref) for customizing the default cache creation for `source`.
