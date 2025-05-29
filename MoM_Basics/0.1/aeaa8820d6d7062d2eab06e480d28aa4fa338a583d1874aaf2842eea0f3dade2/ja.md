```
globalrvec2Local(rvecglobal::Vec3D{T}, l2gRot::StaticMatrix{3,3, FT}) where {T<:Number, FT<:Real}
```

計算全局ベクトル `rvecglobal` が与えられた局所から全体への座標回転行列 `l2gRot` の下での局所座標。
