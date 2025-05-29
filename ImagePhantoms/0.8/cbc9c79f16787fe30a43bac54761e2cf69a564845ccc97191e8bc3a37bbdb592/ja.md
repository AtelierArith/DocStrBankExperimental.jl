```
spectrum(fx::Vector, fy::Vector, fz::Vector, oa::Array{<:Object3d})
```

`(fx,fy,fz)` の位置でサンプリングされた 3D k 空間配列を返します。返される 3D 配列のサイズは `length(fx) × length(fy) × length(fz)` です。
