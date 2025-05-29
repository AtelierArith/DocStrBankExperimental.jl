```
normal(surf::ParametricSurface{T}, u::T, v::T) -> SVector{3,T}
normal(surf::ParametricSurface{T}, uv::SVector{2,T}) -> SVector{3,T}
```

指定された uv 座標で `surf` の法線を返します。
