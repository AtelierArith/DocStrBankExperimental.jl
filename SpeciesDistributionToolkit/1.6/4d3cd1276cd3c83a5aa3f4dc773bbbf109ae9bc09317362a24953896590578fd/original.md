```
zone(layer::SDMLayer, polygons::Vector{T}) where {T <: Union{Polygon,MultiPolygon,Feature,FeatureCollection}}
```

Returns a layer in which the value of each pixel is set to the index of the polygon to which it belongs. Initially valued cells that are not part of a polygon are turned off.
