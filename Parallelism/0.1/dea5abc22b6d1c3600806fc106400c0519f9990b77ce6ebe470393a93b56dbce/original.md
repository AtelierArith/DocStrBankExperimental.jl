```
tmap_with_warmup(f, xs...; basesize=1)
```

Similar to [`tmap`](@ref), but runs the first call single threaded, before multithreading the remainnder. This is useful for dealing with things that benifit from something happening on first run. Which might be related to caching values, or some compilation troubles.

`basesize` controls the minimum number of items from `xs` to process per `@spawn`ed task.

See [`tmap`](@ref) for more details
