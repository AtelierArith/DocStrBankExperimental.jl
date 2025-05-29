```
Pool{T}(limit::Int=4096)
Pool{K, T}(limit::Int=4096)
```

A threadsafe object for managing a pool of objects of type `T`, optionally keyed by objects of type `K`.

Objects can be requested by calling `acquire(f, pool, [key])`, where `f` is a function that returns a new object of type `T`. The `key` argument is optional and can be used to lookup objects that match a certain criteria (a `Dict` is used internally, so matching is `isequal`).

The `limit` argument will limit the number of objects that can be in use at any given time. If the limit has been reached, `acquire` will block until an object is released via `release`.

  * `release(pool, obj)` will return the object to the pool for reuse.
  * `release(pool)` will decrement the number in use but not return any object for reuse.
  * `drain!` can be used to remove objects that have been returned to the pool for reuse; it does *not* release any objects that are in use.

See also `acquire`, `release`, `Pools.limit`, `Pools.in_use`, `Pools.in_pool`, `drain!`. The key and object types can be inspected with `keytype` and `valtype` respectively.
