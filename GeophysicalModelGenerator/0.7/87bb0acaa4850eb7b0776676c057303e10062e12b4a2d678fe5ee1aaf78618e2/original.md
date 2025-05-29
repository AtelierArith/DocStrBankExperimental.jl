```
Surf_interp = interpolate_datafields_2D(V::GeoData, x::AbstractRange, y::AbstractRange;  Lat::Number, Lon::Number)
```

Interpolates a 3D data set `V` with a projection point `proj=(Lat, Lon)` on a plane defined by `x` and `y`, where `x` and `y` are uniformly spaced. Returns the 2D array `Surf_interp`.
