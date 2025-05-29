```
ExpiringCaches.Cache{K, V}(timeout::Dates.Period; purge_on_timeout::Bool=false)
```

Create a thread-safe, expiring cache where values older than `timeout` are "invalid" and will be deleted.

An `ExpiringCaches.Cache` is an `AbstractDict` and tries to emulate a regular `Dict` in all respects. It is most useful when the cost of retrieving or calculating a value is expensive and is able to be "cached" for a certain amount of time. To avoid using the cache (i.e. to invalidate the cache), a `Cache` supports the `delete!` and `empty!` methods to remove values manually.

By default, expired keys will remain in the cache until requested (via `haskey` or `get`); if `purge_on_timeout=true` keyword argument is passed, then an async task will be spawned for each key upon entry. When the timeout task has waited `timeout` length of time, the key will be removed from the cache.
