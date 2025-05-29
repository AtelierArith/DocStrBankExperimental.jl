```
partials(surf::ParametricSurface{T}, u::T, v::T) -> (SVector{3,T}, SVector{3,T})
partials(surf::ParametricSurface{T}, uv::SVector{2,T}) -> (SVector{3,T}, SVector{3,T})
```

指定されたuv座標におけるuおよびvに関する`surf`の3D偏微分のタプルを返します。
