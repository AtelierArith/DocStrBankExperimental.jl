```
bilinear(x, y, z::AbstractArray{T,3}, xx, yy; na_rm=true, parallel=true, progress=true) where {T<:Real}
bilinear(x, y, z::AbstractArray{T,3}; b::bbox, reverse_lat=true, cellsize=1, na_rm=true)
bilinear(ra::SpatRaster{T,3}; cellsize=1, na_rm=true, kw...) where {T<:Real}
```

位置 (locx, locy) が x と y の最初の 2 つのグリッドポイントの間にあると仮定します。つまり、locx は x1 と x2 の間にあり、locy は y1 と y2 の間にあります。`ex= (l1-x1)/(x2-x1)` `ey= (l2-y1)/(y2-y1)` とします。補間は次のようになります。

( 1-ex)(1-ey)*z11 + (1- ex)(ey)*z12 + ( ex)(1-ey)*z21 + ( ex)(ey)*z22

ここで、z は Z 行列の対応する要素です。

```julia
bilinear(x, y, z, xx, yy; na_rm, parallel, progress)
```

[`packages/NetCDFTools/QX4TD/src/Interpolation/bilinear.jl:34`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/Interpolation/bilinear.jl) で定義されています。

! 補間外延、可能性があるエラーを引き起こすことがあります！

# 参考文献

1. https://github.com/NCAR/fields/blob/master/fields/R/interp.surface.R#L48
2. https://en.wikipedia.org/wiki/Bilinear_interpolation

# 例

```jldoc
lon = 70:5:140
lat = 15:5:55

Lon = 70:2.5:140
Lat = 15:2.5:55
Z = rand(T, length(lon), length(lat), 2)
r = bilinear(lon, lat, Z, Lon, Lat; na_rm=true)
```
