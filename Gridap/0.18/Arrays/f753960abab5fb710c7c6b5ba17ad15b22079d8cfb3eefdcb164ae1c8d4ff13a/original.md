```
evaluate!(cache,f,x...)
```

Applies the mapping `f` at the arguments `x...` using the scratch data provided in the given `cache` object. The `cache` object is built with the [`return_cache`](@ref) function using arguments of the same type as in `x`. In general, the returned value `y` can share some part of its state with the `cache` object. If the result of two or more calls to this function need to be accessed simultaneously (e.g., in multi-threading), create and use several `cache` objects (e.g., one cache per thread).
