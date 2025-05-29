```
sphere2cart(coor_sphere::AbstractVector{T}) where T<:Real
sphere2cart(coor_sphere...)
sphere2cart(r::T, θϕ::θϕInfo{T}) where T<:Real
```

球座標 `coor_sphere` を直交座標に変換します。
