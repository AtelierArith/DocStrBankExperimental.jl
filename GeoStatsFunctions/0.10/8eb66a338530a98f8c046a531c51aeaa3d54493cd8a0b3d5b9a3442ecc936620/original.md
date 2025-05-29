```
PlanarTransiogram(normal, data, var; ntol=1e-6u"m", [options])
```

Computes the empirical transiogram for the categorical variable `var` stored in geospatial `data` along a plane perpendicular to a `normal` direction with plane tolerance `ntol` in length units.

Forwards `options` to the underlying [`EmpiricalTransiogram`](@ref).
