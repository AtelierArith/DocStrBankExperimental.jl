```
pop(d::AbstractSmallDict{N,K,V}, key, default::U) where {N,K,V,U} -> Tuple{SmallDict{N,K,V}, Union{V,U}}
```

If `d` has the key `key`, remove it and return the new dictionary together with `d[key]`. Otherwise return the tuple `(SmallDict(d), default)`.

See also `Base.pop!`.
