```
localrvec2Global(rvecslocal::Vec3D{T}, l2gRot::StaticMatrix{3,3, FT}, r0InGlobal::Vec3D{FT}) where {T<:Number, FT<:Real}
```

計算局部ベクトル `rveclocal` が与えられた局所からグローバル座標の回転行列 `l2gRot` の下でのグローバル座標を、局所座標の原点がグローバル座標の `r0InGlobal` にある場合。
