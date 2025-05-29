```
delete(d::AbstractSmallDict{N,K,V}, key) where {N,K,V} -> SmallDict{N,K,V}
```

Remove the mapping for `key` from `d` (if it exists) and return the new dictionary.

See also `Base.delete!`, [`pop`](@ref pop(::AbstractSmallDict, ::Any)).
