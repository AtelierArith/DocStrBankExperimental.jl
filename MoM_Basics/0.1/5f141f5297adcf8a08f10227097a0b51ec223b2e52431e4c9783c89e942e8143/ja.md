```
localrvec2Global(rvecslocal::Vec3D{T}, l2gRot::StaticMatrix{3,3, FT}) where {T<:Number, FT<:Real}
```

計算局部ベクトル `rveclocal` が与えられた局所からグローバル座標の回転行列 `l2gRot` の下でのグローバル座標。
