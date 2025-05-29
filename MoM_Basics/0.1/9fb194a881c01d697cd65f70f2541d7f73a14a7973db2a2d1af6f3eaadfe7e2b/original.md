```
localrvec2Global(rvecslocal::Matrix{T}, l2gRot::StaticMatrix{3,3, FT}) where {T<:Number, FT<:Real}
```

计算局部向量组成的矩阵 `rvecslocal` 在给定局部至全局坐标旋转矩阵 `l2gRot` 下的全局坐标。
