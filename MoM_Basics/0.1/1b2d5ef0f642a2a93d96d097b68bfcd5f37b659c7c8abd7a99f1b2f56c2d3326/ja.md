```
getNodeTriTetraHexaVtk(pathname::ST; FT::Type{T}=Precision.FT, meshUnit = :m) where {ST <: AbstractString,T<:AbstractFloat}
```

`.vtk` ファイルからノード座標、三角形点、四面体点、六面体点（現在は六面体はサポートされていません）を読み取ります。
