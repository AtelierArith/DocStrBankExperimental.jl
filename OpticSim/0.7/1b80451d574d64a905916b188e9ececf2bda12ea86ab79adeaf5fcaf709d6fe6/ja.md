```
onsurface(obj::CSGTree{T}, point::SVector{3,T}) -> Bool
onsurface(obj::CSGTree{T}, x::T, y::T, z::T) -> Bool
```

3D空間の点が`obj`の表面（すなわちシェル）上にあるかどうかをテストします。
