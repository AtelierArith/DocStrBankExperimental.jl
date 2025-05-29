```
GeoArray(A::AbstractArray{T,2|3} where T <: NumberOrMissing, f::AffineMap, crs::String)
```

Construct a GeoArray from any Array and an `AffineMap` that specifies the coordinates and `crs` string in WKT format.
