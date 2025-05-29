```
PlanarVariogram(normal, data, var₁, var₂=var₁; ntol=1e-6u"m", [options])
```

Computes the empirical (cross-)variogram for the variables `var₁` and `var₂` stored in geospatial `data` along a plane perpendicular to a `normal` direction with plane tolerance `ntol` in length units.

Forwards `options` to the underlying [`EmpiricalVariogram`](@ref).
