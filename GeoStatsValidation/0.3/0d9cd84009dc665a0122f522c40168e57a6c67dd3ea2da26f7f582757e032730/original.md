```
cverror(model::GeoStatsModel, geotable, method; kwargs...)
```

Estimate cross-validation error of geostatistical `model` on given `geotable` with error estimation `method` using `Interpolate` or `InterpolateNeighbors` depending on `kwargs`.

```
cverror(model::StatsLearnModel, geotable, method)
cverror((model, feats => targs), geotable, method)
```

Estimate cross-validation error of statistical learning `model` on given `geotable` with error estimation `method`.
