```
getknnresult(k::Integer, ctx::AbstractContext) -> KnnResult
```

Generic function to obtain a shared result set for the same thread and avoid memory allocations. This function should be specialized for indexes and caches that use shared results or threads in some special way.
