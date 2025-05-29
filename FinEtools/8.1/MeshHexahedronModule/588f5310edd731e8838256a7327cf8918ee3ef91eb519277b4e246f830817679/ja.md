```
H8voximg(
    img::Array{DataT,3},
    voxdims::Vector{T},
    voxval::Array{DataT,1},
) where {DataT<:Number}
```

三次元画像から六面体メッシュを生成します。
