```
position_angle(c1::AbstractSkyCoords, c2::AbstractSkyCoords) -> angle
```

2つの天球座標間の位置角を返します。正のラジアンで表されます。

# 例

```jldoctest
julia> c1 = ICRSCoords(0, 0); c2 = ICRSCoords(deg2rad(1), 0);

julia> position_angle(c1, c2) |> rad2deg
90.0
```
