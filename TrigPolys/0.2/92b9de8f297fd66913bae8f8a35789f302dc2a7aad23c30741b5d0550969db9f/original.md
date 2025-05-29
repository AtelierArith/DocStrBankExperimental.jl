```
TrigPoly(u::AbstractVector{T}) where {T<:AbstractFloat}
```

Constructs a `TrigPoly` given a vector of coefficients of length `2n+1`. The first entry of `u` is `a0`, the next `n` entries are `ac` and the last `n` entries are `as`.
