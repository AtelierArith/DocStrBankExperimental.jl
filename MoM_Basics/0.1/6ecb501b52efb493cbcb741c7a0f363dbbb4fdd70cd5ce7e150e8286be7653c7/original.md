```
sphere2cart(coor_sphere::AbstractVector{T}) where T<:Real
sphere2cart(coor_sphere...)
sphere2cart(r::T, θϕ::θϕInfo{T}) where T<:Real
```

将球坐标 `coor_sphere` 转换到直角坐标。
