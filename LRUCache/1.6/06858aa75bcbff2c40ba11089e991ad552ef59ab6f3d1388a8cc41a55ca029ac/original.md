```
cache_info(lru::LRU) -> CacheInfo
```

Returns a `CacheInfo` object holding a snapshot of information about the cache hits, misses, current size, and maximum size, current as of when the function was called. To access the values programmatically, use property access, e.g. `info.hits`.

Note that only `get!` and `get` contribute to hits and misses, and `empty!` resets the counts of hits and misses to 0.

## Example

```jldoctest
lru = LRU{Int, Float64}(maxsize=10)

get!(lru, 1, 1.0) # miss

get!(lru, 1, 1.0) # hit

get(lru, 2, 2) # miss

get(lru, 2, 2) # miss

info = cache_info(lru)

# output

CacheInfo(; hits=1, misses=3, currentsize=1, maxsize=10)
```
