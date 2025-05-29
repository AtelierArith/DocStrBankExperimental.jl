```
globalrvec2Local(rvecglobal::Vec3D{T}, l2gRot::StaticMatrix{3,3, FT}) where {T<:Number, FT<:Real}
```

计算全局向量 `rvecglobal` 在给定局部至全局坐标旋转矩阵 `l2gRot` 下的局部坐标。
