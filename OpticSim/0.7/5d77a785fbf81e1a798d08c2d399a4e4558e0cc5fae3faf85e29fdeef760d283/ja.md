```
point(surf::ParametricSurface{T}, u::T, v::T) -> SVector{3,T}
point(surf::ParametricSurface{T}, uv::SVector{2,T}) -> SVector{3,T}
```

指定されたuv座標で`surf`上の3Dポイントを返します。
