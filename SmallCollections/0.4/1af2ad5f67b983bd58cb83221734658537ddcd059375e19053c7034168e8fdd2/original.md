```
pop(s::AbstractSmallSet{N,T}) where {N,T} -> Tuple{SmallSet{N,T}, T}
```

Remove an element `x` from `s` and return the new set together with `x`. The set `s` must not be empty.

See also `Base.pop!`.
