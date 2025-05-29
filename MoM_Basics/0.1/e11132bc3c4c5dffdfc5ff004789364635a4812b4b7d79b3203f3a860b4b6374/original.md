```
globalrvec2Local(rvecsglobal::Matrix{T}, l2gRot::StaticMatrix{3,3, FT}, r0InGlobal::Vec3D{FT}) where {T<:Number, FT<:Real}
```

计算全局向量组成的矩阵 `rvecsglobal` 在给定局部至全局坐标旋转矩阵 `l2gRot` 下的局部坐标，局部坐标的原点在全局坐标的 `r0InGlobal` 处。
