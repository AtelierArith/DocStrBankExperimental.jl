```
localrvec2Global(rvecslocal::Matrix{T}, l2gRot::StaticMatrix{3,3, FT}, r0InGlobal::Vec3D{FT}) where {T<:Number, FT<:Real}
```

計算局部ベクトルで構成された行列 `rvecslocal` が、与えられた局所からグローバル座標への回転行列 `l2gRot` の下でのグローバル座標を、局所座標の原点がグローバル座標の `r0InGlobal` にある場合。
