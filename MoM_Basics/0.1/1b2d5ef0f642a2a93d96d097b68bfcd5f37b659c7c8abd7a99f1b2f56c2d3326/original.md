```
getNodeTriTetraHexaVtk(pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :m) where {ST <: AbstractString,T<:AbstractFloat}
```

读取 `.vtk` 文件中的节点坐标、三角形点、四面体点、六面体点(目前不支持六面体)。
