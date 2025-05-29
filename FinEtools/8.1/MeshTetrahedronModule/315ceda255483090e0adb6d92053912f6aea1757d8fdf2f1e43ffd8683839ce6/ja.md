```
T4voximg(
    img::Array{DataT,3},
    voxdims::T,
    voxval::Array{DataT,1},
) where {DataT<:Number, T}
```

三次元画像から四面体メッシュを生成します。
