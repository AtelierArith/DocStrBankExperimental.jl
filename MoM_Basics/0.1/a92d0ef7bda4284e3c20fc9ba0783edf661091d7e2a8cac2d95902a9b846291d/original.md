```
sourceEfield(sources::Vector{ST}, rvec::AbstractVector{FT}) where {FT<:Real, ST<:ExcitingSource}
```

计算源向量 `sources` 在全局坐标下给定位置 `rvec` 处的远场电场。
