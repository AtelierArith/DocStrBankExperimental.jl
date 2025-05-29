```
inside(surf::ParametricSurface{T}, p::SVector{3,T}) -> Bool
inside(surf::ParametricSurface{T}, x::T, y::T, z::T) -> Bool
```

3D空間の点が`surf`の*内部*にあるかどうかをテストします。
