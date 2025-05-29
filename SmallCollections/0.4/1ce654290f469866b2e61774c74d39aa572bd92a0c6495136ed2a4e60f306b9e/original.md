```
setindex(d::AbstractSmallDict{N,K,V}, val, key) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

Return the dictionary that is obtained from `d` by adding the mapping `key => val`.

See also `Base.setindex!`, [`push`](@ref push(::AbstractSmallDict, ::Pair)).
