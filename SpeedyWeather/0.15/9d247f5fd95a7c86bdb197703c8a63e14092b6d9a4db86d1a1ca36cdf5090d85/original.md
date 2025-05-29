Seasonal ocean climatology that reads monthly sea surface temperature fields from file, and interpolates them in time regularly (default every 3 days) to be stored in the prognostic variables. Fields and options are

  * `nlat_half::Int64`: number of latitudes on one hemisphere, Equator included
  * `path::String`: [OPTION] Path to the folder containing the sea surface temperatures, pkg path default
  * `file::String`: [OPTION] Filename of sea surface temperatures
  * `varname::String`: [OPTION] Variable name in netcdf file
  * `file_Grid::Type{<:SpeedyWeather.RingGrids.AbstractGrid}`: [OPTION] Grid the sea surface temperature file comes on
  * `missing_value::Any`: [OPTION] The missing value in the data respresenting land
  * `monthly_temperature::Any`: Monthly sea surface temperatures [K], interpolated onto Grid
