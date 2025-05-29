```
push(s::AbstractSmallSet{N,T}, xs...) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

Return the set that is obtained from `s` by adding the elements given as arguments.

See also `Base.push!`.
