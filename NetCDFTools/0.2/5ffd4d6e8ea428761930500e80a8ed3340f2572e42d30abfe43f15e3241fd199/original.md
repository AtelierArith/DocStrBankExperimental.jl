```
bilinear(x, y, z::AbstractArray{T,3}, xx, yy; na_rm=true, parallel=true, progress=true) where {T<:Real}
bilinear(x, y, z::AbstractArray{T,3}; b::bbox, reverse_lat=true, cellsize=1, na_rm=true)
bilinear(ra::SpatRaster{T,3}; cellsize=1, na_rm=true, kw...) where {T<:Real}
```

Suppose that the location, (locx, locy) lies in between the first two grid points in both x an y. That is locx is between x1 and x2 and locy is between y1 and y2. Let `ex= (l1-x1)/(x2-x1)` `ey= (l2-y1)/(y2-y1)`. The interpolant is

( 1-ex)(1-ey)*z11 + (1- ex)(ey)*z12 + ( ex)(1-ey)*z21 + ( ex)(ey)*z22

Where the z's are the corresponding elements of the Z matrix.

```julia
bilinear(x, y, z, xx, yy; na_rm, parallel, progress)
```

defined at [`packages/NetCDFTools/QX4TD/src/Interpolation/bilinear.jl:34`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/Interpolation/bilinear.jl).

! 插值外延，可能会导致错误！

# References

1. https://github.com/NCAR/fields/blob/master/fields/R/interp.surface.R#L48
2. https://en.wikipedia.org/wiki/Bilinear_interpolation

# Examples

```jldoc
lon = 70:5:140
lat = 15:5:55

Lon = 70:2.5:140
Lat = 15:2.5:55
Z = rand(T, length(lon), length(lat), 2)
r = bilinear(lon, lat, Z, Lon, Lat; na_rm=true)
```
