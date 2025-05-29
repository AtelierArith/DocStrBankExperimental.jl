```julia
NEI2016MonthlyEmis(sector, domaininfo; scale, name, stream)

```

A data loader for CMAQ-formatted monthly US National Emissions Inventory data for year 2016, available from: https://gaftp.epa.gov/Air/emismod/2016/v1/gridded/monthly_netCDF/. The emissions here are monthly averages, so there is no information about diurnal variation etc.

`spatial_ref` should be the spatial reference system that the simulation will be using. `x` and `y`, and should be the coordinate variables and grid spacing values for the simulation that is going to be run, corresponding to the given x and y values of the given `spatial_ref`, and the `lev` represents the variable for the vertical grid level. x and y must be in the same units as `spatial_ref`.

`dtype` represents the desired data type of the interpolated values. The native data type for this dataset is Float32.

`scale` is a scaling factor to apply to the emissions data. The default value is 1.0.

`stream` specifies whether the data should be streamed in as needed or loaded all at once.

NOTE: This is an interpolator that returns an emissions value by interpolating between the centers of the nearest grid cells in the underlying emissions grid, so it may not exactly conserve the total emissions mass, especially if the simulation grid is coarser than the emissions grid.
