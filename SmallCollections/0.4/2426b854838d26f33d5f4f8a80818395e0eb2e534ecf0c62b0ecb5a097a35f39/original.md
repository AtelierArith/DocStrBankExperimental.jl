```
pop(s::AbstractSmallSet{N,T}, x, default::U) where {N,T,U} -> Tuple{SmallSet{N,T}, Union{T,U}}
```

If `s` has the element `x`, remove it and return the new set together with the stored element equal to `x`. Otherwise return the tuple `(SmallSet(d), default)`.

See also `Base.pop!`.
