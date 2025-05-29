```
popfirst(v::V) where {T, V <: AbstractCapacityVector{T}} -> Tuple{V,T}
```

Return the tuple `(w, x)` where `x` is the first element of `v` and `w` obtained from `v` by dropping this element. The vector `v` must not be empty.

See also `Base.popfirst!`, `BangBang.popfirst!!`.
