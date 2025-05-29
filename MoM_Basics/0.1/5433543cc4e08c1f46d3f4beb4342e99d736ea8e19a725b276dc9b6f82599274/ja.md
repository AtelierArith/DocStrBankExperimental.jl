```
getNodeElems(::Val{:NAS}, pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :mm) where {ST <: AbstractString,T<:AbstractFloat}
```

.nasファイルからノード座標、三角形点、四面体点、六面体点を読み取ります。
