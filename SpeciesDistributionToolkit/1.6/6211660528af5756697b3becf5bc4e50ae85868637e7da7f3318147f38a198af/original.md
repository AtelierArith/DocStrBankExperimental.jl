```
trim(layer::SDMLayer, feature::T) where {T <: GeoJSON.GeoJSONT}
```

Return a trimmed version of a layer, according to the feature defined a `GeoJSON` object. The object is first masked according to the `feature`, and then trimmed.
