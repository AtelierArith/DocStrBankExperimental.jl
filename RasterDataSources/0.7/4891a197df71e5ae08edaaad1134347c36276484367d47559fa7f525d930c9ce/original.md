```
BioClim <: RasterDataSet
```

BioClim datasets. Usually containing layers from `1:19`.  These can also be accessed with `:bioX`, e.g. `:bio5`.

They do not usually use `month` or `date` keywords, but may use `date` in past/future scenarios. 

Currently implemented for WorldClim and CHELSA as `WorldClim{BioClim}`, `CHELSA{BioClim}` and `CHELSA{Future{BioClim, args..}}`.

See the [`getraster`](@ref) docs for implementation details.
