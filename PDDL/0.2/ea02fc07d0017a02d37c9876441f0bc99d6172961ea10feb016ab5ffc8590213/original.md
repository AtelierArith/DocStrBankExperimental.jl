```
CachedDomain(source::Domain)
CachedDomain(source::Domain, method_keys)
```

Construct a `CachedDomain` from a `source` domain, along with the associated caches for each cached method. A list of `method_keys` can be provided, where each key is a `Symbol` specifying the method to be cached.

By default, the following methods are cached: `[:available, :relevant, :infer_static_fluents, :infer_affected_fluents, :infer_axiom_hierarchy]`.
