```
pop(d::AbstractSmallDict{N,K,V}, key) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

Remove the mapping for `key` from `d` and return the new dictionary together with the value `d[key]`.

See also `Base.pop!`, [`delete`](@ref delete(::AbstractSmallDict, ::Any)).
