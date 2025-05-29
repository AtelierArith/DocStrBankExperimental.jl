```
TrigPoly(u::AbstractVector{T}) where {T<:AbstractFloat}
```

長さ `2n+1` の係数のベクトルから `TrigPoly` を構築します。`u` の最初のエントリは `a0` で、次の `n` エントリは `ac`、最後の `n` エントリは `as` です。
