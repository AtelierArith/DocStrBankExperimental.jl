```
offset(::AbstractSkyCoords, AbstractSkyCoords) -> angle, angle
```

2つの天球座標間の分離と位置角をラジアンで返します。

# 例

```jldoctest
julia> c1 = ICRSCoords(0, 0); c2 = ICRSCoords(deg2rad(1), 0);

julia> offset(c1, c2) .|> rad2deg
(1.0, 90.0)
```

# 参照

  * [`separation`](@ref), [`position_angle`](@ref)
