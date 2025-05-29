```
modify(img::IntensityMap, transforms...)
```

This modifies the `img` by applying the `transforms...` returning a transformed `IntensityMap`

!!! note



Unlike when `modify` is applied to a `<:AbstractModel` this returns an already modified image.
