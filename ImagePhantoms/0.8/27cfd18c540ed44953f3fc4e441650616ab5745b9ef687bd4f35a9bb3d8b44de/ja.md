```
phantom(x::Vector, y::Vector, oa::Array{<:Object2d})
```

グリッドの `(x,y)` 位置でサンプリングされたファントムの2Dデジタル画像を返します。返される2D画像のサイズは `length(x) × length(y)` です。
