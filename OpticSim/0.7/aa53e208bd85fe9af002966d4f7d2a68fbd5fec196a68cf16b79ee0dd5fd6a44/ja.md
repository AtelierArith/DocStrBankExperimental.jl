```
uv(surf::ParametricSurface{T}, p::SVector{3,T}) -> SVector{2,T}
uv(surf::ParametricSurface{T}, x::T, y::T, z::T) -> SVector{2,T}
```

3D空間の点`p`の`surf`上のuv座標を返します。`onsurface(surf, p)`がfalseの場合、動作は未定義であり、不正確なuv、無効なuv、NaNを返すか、クラッシュする可能性があります。
