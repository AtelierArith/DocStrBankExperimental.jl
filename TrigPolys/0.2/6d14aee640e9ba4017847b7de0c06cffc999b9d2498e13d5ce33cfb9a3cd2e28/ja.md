```
pad_to(p::TrigPoly{T,VT}, n::Integer) where {T<:AbstractFloat, VT<:AbstractVector{T}}
```

`p.ac` と `p.as` の長さを `n` に増やし、必要に応じてゼロでパディングします。`n` は `p.n` より小さくすることはできません。
