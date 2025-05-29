```
threadids(; threadpool = :default)
```

Get the IDs of the Julia threads in the given threadpool.

Beyond `:default` and `:interactive` the `threadpool` keyword argument may be set to `:all` (for `:default` + `:interactive` threads) and `:gc` (for GC threads). Note that the latter option is only experimental at this point and might change or go away at any point.
