```
ERA5Dataset
```

Abstract supertype for ERA5 reanalysis datasets, with the following subtypes:

```
ERA5CDStore <: ERA5Dataset
ERA5Custom  <: ERA5Dataset
ERA5Dummy   <: ERA5Dataset
```

All `ERA5Dataset` Types contain the following fields:

  * `path` : The specified directory in which to save the data
  * `emask` : The specified directory in which to save the `LandSea` dataset

All `ERA5CDStore` and `ERA5Custom` Types also contain the following additional fields:

  * `ID` : The module ID, that also acts as a prefix to filenames
  * `name` : The full name of the module
  * `start` : The date for which downloads/analysis begins
  * `stop` : The date for which downloads/analysis finishes
  * `sldoi` : Single-Level DOI (N/A for ERA5Daily)
  * `pldoi` : Pressure-Level DOI (N/A for ERA5Daily)
  * `ptype` : Product type (N/A for ERA5Daily), set to `reanalysis`
