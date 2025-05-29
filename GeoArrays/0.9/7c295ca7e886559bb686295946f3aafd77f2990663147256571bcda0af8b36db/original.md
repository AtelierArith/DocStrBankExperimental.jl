```
GeoArray(A::AbstractArray{T,3} where T <: NumberOrMissing, f::AffineMap)
```

Construct a GeoArray from any Array and an `AffineMap` that specifies the coordinates. A default `CRS` will be generated.
