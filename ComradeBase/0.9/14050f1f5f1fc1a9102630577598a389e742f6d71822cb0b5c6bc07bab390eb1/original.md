```
intensitymap(model::AbstractModel, dims::AbstractDomain)
```

Computes the intensity map or *image* of the `model`. This returns an `IntensityMap` which is a `IntensityMap` with `dims` an [`AbstractDomain`](@ref) as dimensions.
