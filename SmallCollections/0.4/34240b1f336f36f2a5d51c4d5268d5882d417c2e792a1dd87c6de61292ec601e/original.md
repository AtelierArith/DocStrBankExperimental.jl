```
pop(d::AbstractSmallDict{N,K,V}) where {N,K,V} -> Tuple{SmallDict{N,K,V}, Pair{K,V}}
```

Remove a mapping `key => val` from `d` and return the new dictionary together with the mapping. The dictionary `d` must not be empty.

See also `Base.pop!`.
