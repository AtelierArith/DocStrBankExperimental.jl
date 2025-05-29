```
CacheFilter(f::Function) -> CacheFilter
```

Only store value `v` at key `k` if `f(v) === true` (`k` is always `v.id`).
