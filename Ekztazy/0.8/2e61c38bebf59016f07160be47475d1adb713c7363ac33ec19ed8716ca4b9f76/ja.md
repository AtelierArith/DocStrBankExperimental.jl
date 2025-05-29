```
CacheFilter(f::Function) -> CacheFilter
```

値 `v` をキー `k` にのみ格納するのは、`f(v) === true` の場合のみです（`k` は常に `v.id` です）。
