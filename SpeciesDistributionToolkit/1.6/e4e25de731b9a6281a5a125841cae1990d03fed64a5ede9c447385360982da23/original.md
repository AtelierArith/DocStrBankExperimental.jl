```
SimpleSDMLayers.mask!(layer::SDMLayer, poly::T) where T<:Union{Polygon,MultiPolygon}
```

Turns off all the cells outside the polygon (or within holes in the polygon). This modifies the object.
