```
popat(v::V, i::Integer) where {T, V <: AbstractCapacityVector{T}} -> Tuple{V,T}
```

Return the tuple `(w, x)` where `w` obtained from `v` by deleting the element `x` at position `i`. The latter must be between `1` and `length(v)`.

See also `Base.popat!`, `BangBang.popat!!`.
