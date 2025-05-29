```
pad_to(p::TrigPoly{T,VT}, n::Integer) where {T<:AbstractFloat, VT<:AbstractVector{T}}
```

Increase the length of `p.ac` and `p.as` to `n`, padding with zeros if necessary. `n` cannot be smaller than `p.n`.
