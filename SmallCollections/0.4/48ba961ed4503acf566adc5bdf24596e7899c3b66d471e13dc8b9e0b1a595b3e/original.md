```
push(d::AbstractSmallDict{N,K,V}, key1 => val1, key2 => val2, ...) where {N,K,V} -> Tuple{SmallDict{N,K,V}, V}
```

Return the dictionary that is obtained from `d` by adding the mappings given as arguments.

See also `Base.push!`, [`setindex`](@ref setindex(::AbstractSmallDict, ::Any, ::Any)).
