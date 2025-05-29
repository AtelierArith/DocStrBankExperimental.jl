```
inside(obj::CSGTree{T}, point::SVector{3,T}) -> Bool
inside(obj::CSGTree{T}, x::T, y::T, z::T) -> Bool
```

3D空間の点が`obj`の*内部*にあるかどうかをテストします。
