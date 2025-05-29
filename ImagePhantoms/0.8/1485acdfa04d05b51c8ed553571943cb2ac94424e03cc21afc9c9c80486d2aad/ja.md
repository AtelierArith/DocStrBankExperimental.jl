```
phantom(x::Vector, y::Vector, z::Vector, oa::Array{<:Object3d})
```

グリッドの `(x,y,z)` 位置でサンプリングされたファントムの3Dデジタル画像を返します。返される3D画像のサイズは `length(x) × length(y) × length(z)` です。
