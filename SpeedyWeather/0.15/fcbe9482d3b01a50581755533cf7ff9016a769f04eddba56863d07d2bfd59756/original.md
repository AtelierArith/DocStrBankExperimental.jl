Constant ocean climatology that reads monthly sea surface temperature fields from file, and interpolates them only for the initial conditions in time to be stored in the prognostic variables. It is therefore an ocean from climatology but without a seasonal cycle that is constant in time. To be created like

```
ocean = SeasonalOceanClimatology(spectral_grid)
```

and the ocean time is set with `initialize!(model, time=time)`. Fields and options are

  * `path::String`: [OPTION] path to the folder containing the land-sea mask file, pkg path default
  * `file::String`: [OPTION] filename of sea surface temperatures
  * `varname::String`: [OPTION] Variable name in netcdf file
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] Grid the sea surface temperature file comes on
  * `missing_value::Float64`: [OPTION] The missing value in the data respresenting land
