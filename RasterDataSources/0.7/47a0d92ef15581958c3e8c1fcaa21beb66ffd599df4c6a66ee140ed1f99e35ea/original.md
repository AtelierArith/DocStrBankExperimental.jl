```
BioClimPlus <: RasterDataSet
```

Extended BioClim datasets, available from CHELSA.  More information on the CHELSA website: https://chelsa-climate.org/exchelsa-extended-bioclim/

Some of these are available as average annual maximum, minimum, mean, and range.  Others have a single value, more like the regular BioClim variables.

They do not usually use `month` or `date` keywords, but may use `date` in past/future scenarios. 

Currently implemented for CHELSA as `CHELSA{BioClim}` and `CHELSA{Future{BioClim, args..}}`, specifying layer names as `Symbol`s.

See the [`getraster`](@ref) docs for implementation details.
