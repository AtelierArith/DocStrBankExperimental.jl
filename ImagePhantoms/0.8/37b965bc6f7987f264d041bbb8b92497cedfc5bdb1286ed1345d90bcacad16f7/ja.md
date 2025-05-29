```
phantom(x::Vector, y::Vector, oa::Array{<:Object2d}, oversample::Int; T)
```

グリッドの `(x,y)` 位置でサンプリングされたファントムの2Dデジタル画像を返し、オーバーサンプリング係数 `oversample` と要素型 `T` を指定します。
