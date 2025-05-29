```
invget(d::AbstractSmallDict{N,K}, val) where {N,K} -> K
```

Return a key in `d` whose value is equal to `val` (in the sense of `isequal`). If there is no such key, an error is raised.

This reverse lookup is as fast as "forward" lookup by keys. The key returned is the first matching one in `keys(d)`.
