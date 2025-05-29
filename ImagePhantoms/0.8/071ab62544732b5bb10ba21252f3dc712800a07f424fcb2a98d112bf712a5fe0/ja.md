```
image = phantom(x, y, z, oa::Array{<:Object3d}, oversample::Int; T)
```

グリッド `(x,y,z)` の位置でサンプリングされたファントムの3Dデジタル画像を返し、オーバーサンプリング係数 `oversample` と要素型 `T` を指定します。
