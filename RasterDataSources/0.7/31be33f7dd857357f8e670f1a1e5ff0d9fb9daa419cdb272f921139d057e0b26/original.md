```
Weather <: RasterDataSet
```

Weather datasets. These are usually large time-series of specific dates, and use a `date` keyword in `getraster`.

Currently implemented for WorldClim and CHELSA as `WorldClim{Weather}`, and `CHELSA{Weather}`

See the [`getraster`](@ref) docs for implementation details.
