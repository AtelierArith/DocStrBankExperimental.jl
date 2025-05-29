```
ERA5Region
```

Structure that imports relevant [GeoRegion](https://github.com/JuliaClimate/GeoRegions.jl) properties used in the handling of the gridded ERA5 datasets.

The `ERA5Region` Type contain the following fields:

  * `geo` : The `GeoRegion` containing the geographical information
  * `ID` : The ID used to specify the `GeoRegion`
  * `resolution` : The resolution of the gridded data to be downloaded/analysed
  * `string` : Specification of folder and file name, mostly for backend usage
  * `isglb` : A Bool, true if spans the globe, false if no
  * `is360` : True if it spans 360º longitude
