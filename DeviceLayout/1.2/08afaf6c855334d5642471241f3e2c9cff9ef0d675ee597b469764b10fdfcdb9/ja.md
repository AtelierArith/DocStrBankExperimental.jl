```
bounds(s::GeometryStructure{T}) where {T <: Coordinate}
```

構造体または構造体の周りのすべてのオブジェクトを囲む `Rectangle{T}` バウンディングボックスを返します。構造体が空の場合は、幅と高さがゼロの長方形を返します。
