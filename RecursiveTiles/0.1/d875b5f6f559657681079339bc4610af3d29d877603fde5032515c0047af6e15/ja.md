```
Tile{P,T,U,S,N} <: AbstractTile{P,T,U,S,N}
```

具体的なタイル抽象で、インデックス `U<:Tuple{Vararg{S,N}} where {S,N}` を指定します。

参照: [`AbstractTile`](@ref)
