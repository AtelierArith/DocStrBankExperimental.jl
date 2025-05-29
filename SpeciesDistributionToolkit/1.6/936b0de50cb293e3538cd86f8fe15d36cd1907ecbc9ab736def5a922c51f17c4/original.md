```
SimpleSDMLayers.mask(occ::T, poly::P) where {T <: AbstractOccurrenceCollection, P<:Union{Polygon,MultiPolygon}}
```

Returns a copy of the occurrences that are within the polygon.
