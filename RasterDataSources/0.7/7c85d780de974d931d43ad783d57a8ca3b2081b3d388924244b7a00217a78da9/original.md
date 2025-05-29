```
Climate <: RasterDataSet
```

Climate datasets. These are usually months of the year, not specific dates, and use a `month` keyword in `getraster`. They also use `date` in past/future scenarios.

Currently implemented for WorldClim and CHELSA as `WorldClim{Climate}`, `CHELSA{Climate}` and `CHELSA{Future{Climate, args..}}`.

See the [`getraster`](@ref) docs for implementation details.
