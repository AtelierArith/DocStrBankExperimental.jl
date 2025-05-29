```
empty_cache!(
    daf::DafReader;
    [clear::Maybe{CacheGroup} = nothing,
    keep::Maybe{CacheGroup} = nothing]
)::Nothing
```

Clear some cached data. By default, completely empties the caches. You can specify either `clear`, to only forget a specific [`CacheGroup`](@ref) (e.g., for clearing only `QueryData`), or `keep`, to forget everything except a specific [`CacheGroup`](@ref) (e.g., for keeping only `MappedData`). You can't specify both `clear` and `keep`.

!!! note
    If there are any slow cache update operations in flight (matrix relayout, queries) then this will wait until they are done to ensure that the cache is in a consistent state.

