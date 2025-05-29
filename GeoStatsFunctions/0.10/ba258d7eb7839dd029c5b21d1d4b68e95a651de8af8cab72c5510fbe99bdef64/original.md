```
DirectionalTransiogram(direction, data, var; dtol=1e-6u"m", [options])
```

Computes the empirical transiogram for the categorical variable `var` stored in geospatial `data` along a given `direction` with band tolerance `dtol` in length units.

Forwards `options` to the underlying [`EmpiricalTransiogram`](@ref).
