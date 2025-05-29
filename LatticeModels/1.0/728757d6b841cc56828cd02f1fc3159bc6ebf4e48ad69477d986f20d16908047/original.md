```
PointFluxes(fields[; gauge])
```

Construct a `PointFluxes` object from a collection of `PointFlux` objects.

An error is thrown if the gauges of the fields are inconsistent. You can specify the gauge of the field explicitly using the `gauge` keyword argument.

See also: [`PointFlux`](@ref).
