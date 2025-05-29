```
@deferred_fetchval [functions...] block
```

Identical to [`@deferred_fetch`](@ref), but `Future`s have [`fetchval`](@ref) called on them instead of `fetch`.
