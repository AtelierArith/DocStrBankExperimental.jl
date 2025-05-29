```
empty(d::AbstractSmallDict{N,K,V}) where {N,K,V,W} -> AbstractSmallVector{N,K,V}
empty(d::AbstractSmallDict{N,K,V}, W::Type) where {N,K,V,W} -> AbstractSmallVector{N,K,W}
empty(d::AbstractSmallDict{N,K,V}, L::Type, W::Type) where {N,K,V,L,W} -> AbstractSmallVector{N,L,W}
```

Return an empty `AbstractSmallDictionary` with the same capacity as `d`, and with `valtype` changed to `W` and `keytype` changed to `L` if so specified. The resulting dictionary is mutable if and only if `d` is so.
