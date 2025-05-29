```
DirectionalVariogram(direction, data, var₁, var₂=var₁; dtol=1e-6u"m", [options])
```

Computes the empirical (cross-)variogram for the variables `var₁` and `var₂` stored in geospatial `data` along a given `direction` with band tolerance `dtol` in length units.

Forwards `options` to the underlying [`EmpiricalVariogram`](@ref).
