```
getNodeElems(::Val{:NAS}, pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :mm) where {ST <: AbstractString,T<:AbstractFloat}
```

读取 `.nas` 文件中的节点坐标、三角形点、四面体点、六面体点。
